# Zoro — King of Hell — Interactive Reveal

A single-file, interactive "hover-to-reveal" hero page for **Roronoa Zoro**, built with HTML5 Canvas. Move your cursor (or finger, on mobile) across the screen to peel back the base image and reveal his "King of Hell" form underneath, with a soft glowing trail following your pointer.

Inspired by the classic One Piece Gear 5 reveal effect, restyled for Zoro with his own color palette, swords-and-moonlight art, and quotes.

## Preview

| Base state (on load) | Reveal state (cursor moved across) |
|---|---|
| ![Base state — close-up portrait](preview-assets/preview-base.jpg) | ![Reveal state — three-sword moonlit leap](preview-assets/preview-reveal.jpg) |

## Features

- 🖱️ **Cursor/touch-reactive reveal** — a soft circular mask follows the pointer, blending from the base image into the hidden image
- ✨ **Trailing glow effect** — a fading trail of circles creates a smooth "wipe" rather than a hard-edged cutout
- 📱 **Mobile support** — touch events are wired up alongside mouse events
- 🎨 **Custom styling** — green/blue color scheme matching Zoro's design, with `Bangers`, `Bebas Neue`, `Luckiest Guy`, and `Cormorant Garamond` fonts via Google Fonts
- 🖼️ **Zero dependencies** — both images are embedded directly as base64 data URIs, so the page works as a single `.html` file with no separate image assets or build step
- 📐 **Responsive** — canvas resizes on window resize, with a mobile breakpoint for typography/layout

## Usage

1. Download `zoro-king-of-hell.html`
2. Open it directly in any modern browser (double-click, or `open zoro-king-of-hell.html`)
3. Move your mouse (or drag your finger on touch devices) across the image to reveal the King of Hell form

No server, build step, or package install required.

## Repo structure

```
.
├── zoro-king-of-hell.html      # the entire app — open this in a browser
├── README.md
└── preview-assets/
    ├── preview-base.jpg        # screenshot: default state
    └── preview-reveal.jpg      # screenshot: cursor-revealed state
```

The `preview-assets/` images are only used for this README — the HTML file itself has both images embedded inline as base64, so it works standalone without them.

## How it works

- Two images are drawn to **offscreen canvases**: a `bottom` (base) image and a `top` (revealed) image
- On every animation frame, a trail of fading circles is painted onto an offscreen mask canvas, following the smoothed pointer position
- Canvas composite operations (`source-in`, `source-atop`) clip the `top` image to that mask, then layer it over the `bottom` image
- A radial gradient "glow" is drawn at the pointer's current position for extra polish
- The whole loop runs on `requestAnimationFrame` for smooth 60fps tracking<img width="1280" height="720" alt="preview-base" src="https://github.com/user-attachments/assets/23a5477e-5797-4651-98aa-f99c7bb746f7" />
<img width="1280" height="720" alt="preview-reveal" src="https://github.com/user-attachments/assets/f069a04f-8d6e-4ec1-a930-6f0b7dea2d21" />

