# Attention Mechanism 3D Visualization

An interactive 3D visualization demonstrating how the modified attention mechanism affects word embeddings in different contexts.

## Formula

```
softmax(XᵀX + α·diag(XᵀX))·X
```

Where:
- **XᵀX** — computes attention scores between all word vectors
- **α·diag(XᵀX)** — dampening factor that controls self-attention
- **α < 0** — increases self-attention (words stay closer to original position)
- **α > 0** — reduces self-attention (words move more toward context)

## Key Concept

The word **"apple"** starts at the same position `[2, 2, 2]` in both contexts:

### Initial Positions

**Fruit Context:**
| Word | Position |
|------|----------|
| apple | `[2, 2, 2]` |
| orange | `[3.5, 3, 1]` |
| banana | `[4, 1, 2]` |

**Tech Context:**
| Word | Position |
|------|----------|
| apple | `[2, 2, 2]` |
| iPhone | `[2, 1, 3]` |
| Mac | `[1, 3, 0.1]` |

### What happens after attention

| Context | Words | Result |
|---------|-------|--------|
| 🍎 Fruit | apple, orange, banana | apple moves toward fruit cluster |
| 📱 Tech | apple, iPhone, Mac | apple moves toward tech cluster |

This demonstrates how **context changes meaning** — the same word vector gets pulled toward different regions of the embedding space based on surrounding words.

## Features

- **3D vectors with arrows** from origin to each word
- **Draggable spheres** — move any word to see how it affects attention
- **Smooth animations** — watch vectors glide to new positions
- **Ghost spheres** — show original positions after calculation
- **Attention lines** — curved lines show attention weights between words
- **Live position display** — see exact coordinates and changes (Δ)

## Controls

| Action | How |
|--------|-----|
| Rotate view | Drag empty space |
| Zoom | Scroll |
| Move word | Drag sphere |
| Change context | Click Fruit/Tech tabs |
| Adjust dampening | Use α slider |
| Run attention | Click "Calculate Attention" |
| Start over | Click "Reset Positions" |

## Tech Stack

- Three.js (r128)
- OrbitControls
- DragControls
- Pure HTML/CSS/JS

## Credits

Created by collaboration between human designer and **Claude Opus 4.5** (Anthropic).

- **Design & Concept**: Human
- **Code Implementation**: Claude Opus 4.5

---

*This visualization helps understand how attention mechanisms in transformers allow the same word to have different representations based on context.*
