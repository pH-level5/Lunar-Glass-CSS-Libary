# LUNAR GLASS CSS (`lunag.css`)

A darkish, moody modern glassmorphism design libary. This library provides a toned-down, simple, and reusable foundation of layered backdrop-filter glass, ambient scene radials, and SVG-noise grain textures.

LUNAR GLASS CSS originated from "Study Hub", an older studying platform project. While the platform itself was deprecated, the UI components and design system were extracted and curated into this standalone CSS library. Keep in mind that this is not a fully built-up framework; I just curated UI elements from an older project to make them reusable. These elements are set with their own style values, so feel free to customize `lunag.css`.

---

## Special Thanks

| Credit | Author | Source |
|---|---|---|
| Grainy Gradients — SVG `feTurbulence` noise technique | Jimmy Chion | [css-tricks.com/grainy-gradients](https://css-tricks.com/grainy-gradients/) |
| CSS.Glass — Glassmorphism generator & reference | @miketromba | [github.com/miketromba/css.glass](https://github.com/miketromba/css.glass) |
| Fira Code — Monospace font with ligatures | Nikita Prokopov | [fonts.google.com/specimen/Fira+Code](https://fonts.google.com/specimen/Fira+Code) |
| Material Symbols — Icon library | Google Fonts | [fonts.google.com/icons](https://fonts.google.com/icons) |

---

## Quick Start

1. Download [`lunag.css`](css/lunag.css).
2. Include the stylesheet in the `<head>` of your HTML document:

```html
<link rel="stylesheet" href="css/lunag.css">
<!-- Optional: LUNAR GLASS uses Fira Code by default -->
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300..700&display=swap" rel="stylesheet">
<!-- Optional: Material Symbols for icons -->
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" rel="stylesheet">
```

3. Wrap your content in the base scene container:

```html
<body>
    <div class="lna-scene">
        <div class="lna-container">
            <div class="lna-card lna-glass">
                <h1 class="lna-title">Hello World</h1>
                <p>Welcome to LUNAR GLASS.</p>
                <button class="lna-btn lna-glass">Click Me</button>
            </div>
        </div>
    </div>
</body>
```

## Themes

LUNAR GLASS includes four built-in themes that can be applied simply by attaching the corresponding class to the `<body>` element.

- **Default** (No class needed): A sleek, dark glassy aesthetic.
- **Candlelight** (`.lna-candlelight`): A warm, sepia-toned environment with dynamic flickering radial lights mimicking a fire/candle base. Intensity can be controlled via the `--lna-sepia` CSS variable.
- **Coffee** (`.lna-coffee`): A soft, organic brown wash featuring blurred spill shapes behind the glass elements.
- **Moonlit** (`.lna-moon`): A cool, deep blue-grey aesthetic with an optional static starfield and ambient shooting stars (JS injection recommended for full effect).

To switch themes, apply the class to the body tag:

```html
<body class="lna-candlelight">
```

## Core Components

The library relies heavily on utility classes to build up the interface.

### Glass Plates
- `.lna-glass`: Applies the base glassmorphism (translucency, background-blur, minimal shadow/shine).
- `.lna-glass-deep`: Heavier blur variant.
- `.lna-glass-grain`: Applies a tactile surface texture using an SVG `feTurbulence` fractal noise filter.

### Typography
- `.lna-title`: Display heading, bold, uppercase.
- `.lna-heading`: Standard section header with bottom border.
- `.lna-section-label`: Category or context label.
- `.lna-subtitle`, `.lna-muted`: Auxiliary or secondary text.

### Buttons
All buttons use the `.lna-btn` class. Modifier classes adjust the appearance to match context.
- `.lna-btn .lna-glass`: Default glass button. Base styles include an animated radial shine and dot sweep on hover.
- `.lna-btn-primary`: Prominent accent colour.
- `.lna-btn-danger`: Destructive action style.
- `.lna-btn-ghost`: Borderless, non-glassy button with hover state.

### Interactive Elements
- **Inputs**: `.lna-input`, `.lna-textarea`, `.lna-select` provide form controls harmonised with the glass aesthetic.
- **Upload Area**: `.lna-upload` privides a simple instyle upload area, with a mutes dotoed outline.
- **Toggles/Sliders**: Use `.lna-toggle` and `.lna-slider` for standard inputs wrapped in minimalist styling.
- **Progress Bars**: Track interfaces built via `.lna-progress-row`, utilizing `.lna-progress-fill` and a shimmering gradient overlay.

**Example Layering Imputs:**
```css
<div class="lna-form-group">
    <label class="lna-label">Username</label>
    <input type="text" class="lna-input" placeholder="Enter username…">
</div>
```
**Example Layering Upload Area:** 
```css
<label class="lna-upload">
    <span class="material-symbols-outlined" style="font-size:16px;margin-right:8px">upload</span>Upload Avatar
</label>
```

**Example Layering Toggle/Slider:** 
```css
<label class="lna-toggle">
    <input type="checkbox" checked="">
    <span class="lna-toggle-track"></span>
</label>
```

**Example Layering Progressbar:**

```html
<div class="lna-progress-row">
    <span class="lna-progress-label">CS</span>
    <div class="lna-progress-track">
        <div class="lna-progress-fill" data-width="91" style="width: 91%;"></div>
    </div>
    <span class="lna-progress-value">91%</span>
</div>
```

### SVG Matcher

The `.lna-svg` utility wires any SVG to inherit the active theme palette via `currentColor`. All fills, strokes, and text inside the SVG will respond to theme switches automatically.

| Class | Behaviour |
|---|---|
| `.lna-svg` | Inherit all. Sets `fill` and `stroke` to `currentColor`. |
| `.lna-svg-stroke` | Outline/wireframe mode. `fill: none`, `stroke: currentColor`. |
| `.lna-svg-fill` | Solid mode. `fill: currentColor`, `stroke: none`. |
| `.lna-svg-muted` | Forces `color: var(--lna-text-muted)`. |
| `.lna-svg-accent` | Forces `color: var(--lna-accent-soft)`. |
| `.lna-svg-glass` | Semi-transparent fill matching glass surfaces. |
| `.lna-svg-glow` | Adds an animated `drop-shadow` pulse using `currentColor`. |

```html
<!-- Wireframe SVG that themes automatically -->
<svg class="lna-svg lna-svg-stroke" viewBox="0 0 100 100">
    <circle cx="50" cy="50" r="40"/>
    <line x1="10" y1="50" x2="90" y2="50"/>
</svg>

<!-- Solid icon with glow, themed to accent -->
<svg class="lna-svg lna-svg-fill lna-svg-accent lna-svg-glow" viewBox="0 0 24 24">
    <path d="M12 2L2 22h20L12 2z"/>
</svg>
```

### Table

Glass-native table component. Pairs well with `.lna-card.lna-glass`.

| Class | Usage |
|---|---|
| `.lna-table-wrap` | Scrollable outer container. |
| `.lna-table` | Base table styles. |
| `.lna-td-muted` | Muted secondary cell text. |
| `.lna-td-mono` | Tabular numeric formatting. |
| `.lna-td-dot` | Inline status dot. Modifier: `.ok` `.warn` `.danger` `.muted`. |

```html
<div class="lna-table-wrap">
    <table class="lna-table">
        <thead>
            <tr>
                <th>City</th>
                <th>Ping (ms)</th>
                <th>Status</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>London</td>
                <td class="lna-td-mono">8</td>
                <td><span class="lna-td-dot ok">Online</span></td>
            </tr>
            <tr>
                <td>Tokyo</td>
                <td class="lna-td-mono">82</td>
                <td><span class="lna-td-dot warn">Latency</span></td>
            </tr>
        </tbody>
    </table>
</div>
```

## License

This project is licensed under the MIT License. Free to use, modify, and distribute.

