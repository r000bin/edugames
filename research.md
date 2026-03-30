# LLM Education Game - Research

## Existing Inspiration

- **Transformer Explainer** (Georgia Tech) — runs GPT-2 in-browser, lets users see tokenization → embeddings → attention → prediction live. Built with Svelte + D3.js. Uses progressive disclosure (simple overview that expands into detailed views). https://poloclub.github.io/transformer-explainer/
- **Semantle / Contexto** — hugely popular word games built on embedding similarity (players already love this mechanic without knowing what embeddings are). Semantle uses word2vec 300-dimensional cosine similarity. https://legacy.semantle.com/ / https://contexto91.com/
- **Midpoints** — given two words, guess words that bridge the conceptual gap. Scores based on embedding distance. https://stack.convex.dev/midpoints-a-word-game-powered-by-ai-embeddings-and-convex-components
- **TensorFlow Playground** — classic interactive neural net visualization. https://playground.tensorflow.org/
- **MLU Explain** (Amazon) — scrollytelling + interactive visualizations covering ML concepts. Built with Svelte + D3.js. https://mlu-explain.github.io/
- **Nicky Case's Explorable Explanations** — the gold standard for teaching through play. https://blog.ncase.me/explorable-explanations-4-more-design-patterns/
- **BPE Tokenization Visualizer** — step-by-step BPE merge visualization. https://www.bpe-visualizer.com/
- **GPT Tokenizer Playground** — visualizes how text breaks into tokens with color-coding. https://gpt-tokenizer.dev/
- **Temperature Visualizer** — shows top-10 token probabilities and how temperature/top-k change the distribution via sliders. https://andreban.github.io/temperature-topk-visualizer/
- **LLM Sampling Visualizer** — interactive visualization of how temperature, top-p, and top-k affect token selection. https://louis-7.github.io/llm-sampling-visualizer/
- **CMU Word Embedding Demo for K-12** — 3D visualization where students define semantic dimensions with word pairs and explore vector arithmetic. https://ojs.aaai.org/index.php/AAAI/article/view/21548
- **AttentionViz** — global view of transformer attention patterns. https://catherinesyeh.github.io/attn-docs/
- **Educational HTML Games (single-file)** — proves that self-contained single-HTML-file games work well. https://github.com/jkanev/educational-html-games

## Best Design Patterns

1. **"Place Your Bets"** — before revealing the answer, ask the player to predict. Leverages surprise and cognitive dissonance. NYT "You Draw It" is the canonical example. Perfect for next-token prediction.
2. **"Role Play"** — put the player in the position of the system. "You are the LLM" is a powerful frame.
3. **"Puzzle It Out"** — force genuine problem-solving (not following steps). Teaching and assessment happen simultaneously. The learning IS the game mechanic, not a quiz bolted on.
4. **"Sandbox Mode"** — unrestricted exploration. Best with progressive complexity (start simple, unlock features). Good for temperature/sampling exploration.

### Educational Game Design Principles

- **Content-mechanic integration**: The learning IS the gameplay. Do not bolt a quiz onto a game.
- **Progressive disclosure**: Start with the simplest version of the concept. Layer complexity.
- **Immediate visual feedback**: Every player action should produce a visible result. Sliders, drag-and-drop, hover states.
- **Surprise as a teacher**: The "aha moment" when your prediction is wrong is the most powerful learning event.
- **Self-Determination Theory**: games must support competence (I can do this), autonomy (I choose how), and relatedness (I'm not alone).
- **Intrinsic motivation** beats extrinsic rewards for lasting learning.
- **Informative feedback** — not just right/wrong, but why.

## Key LLM Concepts That Can Be Gamified

### Tokenization
How text is split into chunks. Surprise factor: "the" is one token but "Th" + "e" can be two; emojis and non-English text tokenize very differently. Game potential: high, because the results are visual and surprising.

### Next-Token Prediction
The core of how LLMs generate text. Research shows humans are consistently worse than even small models (GPT-2) at predicting the next token. Game potential: extremely high — "guess what comes next" is inherently a game.

### Embeddings / Vector Space
Words as points in space, where distance = similarity. The king-man+woman=queen analogy is the classic hook. Game potential: high — already proven by Semantle and Contexto having large player bases.

### Attention
Which words "look at" which other words. Visualized as heatmaps or connection lines. Game potential: medium — more of an interactive visualization than a game mechanic, but could work as "guess which word is paying attention to which."

### Temperature / Sampling
Slider from deterministic to creative. Game potential: high for a sandbox/exploration mechanic. Players adjust temperature and see wildly different outputs. Very intuitive with a slider UI.

### Context Window
The model can only "see" N tokens at once. Game potential: medium — could be a constraint mechanic (you can only see X words at a time, how well can you understand the story?).

### Hallucination / Confidence
Models can be confidently wrong. Game potential: high — "spot the hallucination" or "is this real or made up?" quiz format.

## Game Ideas (ranked by fun x educational value x feasibility)

### 1. Guess the Next Token
- **Concept taught**: Next-token prediction, probabilities
- **Mechanic**: Sentence builds word-by-word; pick what comes next from 5 options with probability bars. After each round, reveal the full probability distribution.
- **Design pattern**: "Place Your Bets"
- **Complexity**: Medium

### 2. The Tokenizer
- **Concept taught**: Tokenization, BPE
- **Mechanic**: Draw split-lines on text where you think tokens break; reveal actual splits. Levels progress: English → emoji → code → other languages → numbers.
- **Design pattern**: "Puzzle It Out"
- **Complexity**: Low

### 3. Word Space Explorer
- **Concept taught**: Embeddings, similarity
- **Mechanic**: 2D map of words plotted by embedding similarity. Drag words to where they belong. Bonus: vector arithmetic puzzles (king - man + woman = ?). Can use pre-computed Word2Vec/GloVe data reduced to 2D via t-SNE/PCA.
- **Design pattern**: "Puzzle It Out" + "Sandbox"
- **Complexity**: Medium

### 4. Temperature Tuner
- **Concept taught**: Temperature, sampling
- **Mechanic**: Given a goal ("formal email" vs "wild poem"), adjust a slider to pick the best output from pre-computed outputs at different temperatures.
- **Design pattern**: "Sandbox Mode"
- **Complexity**: Low

### 5. Attention Spotlight
- **Concept taught**: Attention mechanism
- **Mechanic**: Show a sentence and highlight one word. Player draws lines to the words they think the model "pays attention to." Reveal actual attention weights as a heatmap.
- **Design pattern**: "Place Your Bets"
- **Complexity**: Medium

### 6. Spot the Hallucination
- **Concept taught**: Hallucination, verification
- **Mechanic**: Show AI-generated paragraphs about real topics. Some facts are correct, some are hallucinated. Player highlights the suspicious claims.
- **Design pattern**: "Role Play" (you are the fact-checker)
- **Complexity**: Low

### 7. Context Window Challenge
- **Concept taught**: Context limits
- **Mechanic**: Read a long story, but you can only see N tokens at a time (sliding window). Answer comprehension questions. As the "context window" grows, questions get easier.
- **Design pattern**: "Role Play" (you experience the LLM's constraints)
- **Complexity**: Low

## Recommended Approach

Build a multi-level game that progresses through concepts in order: **Tokenizer → Next-Token Prediction → Temperature → Embeddings → Attention**. This mirrors how an LLM actually processes text and gives a natural difficulty curve.

## Technical Notes

- **No API calls needed**: All games can work with pre-computed data embedded in the HTML file. Avoids API costs, latency, and authentication.
- **Proven tech stack**: Svelte + D3.js is what Transformer Explainer and MLU Explain use, but vanilla JS + Canvas/SVG works fine for single-file games.
- **Embedding data**: A subset of GloVe embeddings (top 5000 words, reduced to 2D via t-SNE/PCA) can be embedded as JSON — roughly 200KB.
- **Token data**: Pre-computed tokenization results for 50-100 interesting sentences stored as a JSON array.
- **Single-file HTML is viable**: No build step, no dependencies, just open in a browser.
