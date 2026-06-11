# Xenagos Bio — Design System Spec

**Status:** v0.1.

**Source hierarchy (read this first):**
- **The bible (authoritative):** the knowledge base (`knowledge-base/`), the **Tech Direction** doc,
  and the **Corporate Deck (PPT)**. All rules, content, names, and constraints come from these.
- **The mocks (foundation only):** the client coming-soon + homepage comps inform the *visual language*
  (palette, two-tone headline motif, helix imagery, light/dark rhythm) — they are a starting point,
  **not** a source of truth. Where a comp detail conflicts with the bible, the bible wins. Comp-specific
  content (e.g. its placeholder leadership names, "Updates" nav label, sample hero copy) is **disregarded**.

**Confidence:** the hard rules below (responsive range, max-width, breakpoints, componentization, motion,
SEO) come straight from the Tech Direction and are reliable. Color hex, type sizes, and spacing are
**visual direction inferred from the mocks, not sampled from brand-source files** — every value tagged
`⚠confirm` must be validated against real brand assets before final QA.

**Aligns with:** Tech Direction (React + Vite + TypeScript + SCSS; 390→1600px; 3 breakpoints;
1600px content max-width; subtle motion). See `knowledge-base/02-tech-direction.md`.
Content/brand facts (XMS™, pipeline, team, market) come from the deck — see `knowledge-base/03-company-and-science.md`.

---

## 1. Color

### Brand / dark
| Token | Hex `⚠confirm` | Use |
|-------|------|-----|
| `navy-950` | #070F1F | Deepest corners, vignette edges |
| `navy-900` | #0A1A33 | Hero base, primary dark background |
| `navy-800` | #0D1B2E | Dark section background |
| `navy-700` | #122742 | Elevated surfaces / cards on dark |
| `navy-600` | #1B3556 | Borders / dividers on dark (solid) |

### Accent (blue — the only accent; NO teal/green)
| Token | Hex `⚠confirm` | Use |
|-------|------|-----|
| `blue-300` | #7CA8F2 | Secondary accent on dark, subtle highlights |
| `blue-400` | #4A82EE | Hover state for primary |
| `blue-500` | #2F6FE3 | **Primary** — buttons, links, headline line-2 |
| `blue-600` | #2257C4 | Active / pressed |

### Neutrals / light
| Token | Hex `⚠confirm` | Use |
|-------|------|-----|
| `white` | #FFFFFF | Light section base, text on dark |
| `gray-50` | #F6F7F9 | Light section background |
| `gray-100` | #F1F3F5 | Alt light / footer band |
| `gray-200` | #E6E8EC | Hairlines on light |
| `gray-300` | #D4D8DC | Input borders, ghost-button borders |

### Text
| Token | Hex `⚠confirm` | Use |
|-------|------|-----|
| `ink-900` | #1A2230 | Headings on light |
| `ink-600` | #5B6470 | Body on light |
| `ink-400` | #8A929C | Muted / captions on light |
| `on-dark` | #FFFFFF | Headings/body on dark |
| `on-dark-muted` | #9AA6B6 | Body/labels on dark |

### Semantic (forms — Contact page; not in comps, proposed)
`success` #1E9E6A · `error` #D6453B · `warning` #E0922F · `info` = `blue-500`.
Hairline-on-dark: `rgba(255,255,255,0.08)`.

---

## 2. Typography

**Primary typeface:** geometric-humanist sans `⚠confirm exact font` (reads like Figtree / Poppins /
Aspekta family). Comp headlines are light/regular weight. Wordmark in logo lockup is a separate
wide-tracked display caps — not used for UI.

**Weights in use:** 300 (display), 400 (regular), 500 (medium), 600 (semibold eyebrows/buttons).

### Type scale (rem @ 16px base) `⚠confirm sizes`
| Token | Size | Line height | Weight | Tracking | Use |
|-------|------|-------------|--------|----------|-----|
| `display` | 60px / 3.75rem | 1.06 | 300 | -0.02em | Hero H1 |
| `h1` | 48px / 3rem | 1.1 | 300–400 | -0.018em | Page titles |
| `h2` | 40px / 2.5rem | 1.12 | 400 | -0.015em | Section headlines |
| `h3` | 28px / 1.75rem | 1.2 | 500 | -0.01em | Sub-section / card titles |
| `h4` | 20px / 1.25rem | 1.3 | 600 | 0 | Small headings |
| `body-lg` | 18px / 1.125rem | 1.6 | 400 | 0 | Hero sub, lead paragraphs |
| `body` | 16px / 1rem | 1.6 | 400 | 0 | Default body |
| `small` | 14px / 0.875rem | 1.5 | 400 | 0 | Captions, meta, footnotes |
| `eyebrow` | 12px / 0.75rem | 1.4 | 600 | 0.14em | UPPERCASE section labels |

**Two-tone headline pattern (signature, from mocks):** line 1 = `ink-900` (or `on-dark`), line 2 = `blue-500`.
Apply to deck-sourced copy, e.g. "Developing precision guided therapeutics" / "to transform cancer treatment"
or "Transforming" / "precision oncology". (The mock's own wording is reference, not approved copy.)
**Underline accent rule:** ~48px wide, 2px, `blue-500`, sits under headline block.

### Fluid sizing
Display/H1/H2 scale down per breakpoint (don't just compress). Suggested mobile: display 36px,
h1 32px, h2 26px. Use `clamp()` or per-breakpoint overrides.

---

## 3. Spacing

8px base scale: `4, 8, 12, 16, 24, 32, 48, 64, 96, 128`.
Section vertical padding: desktop 96–128px, tablet 72px, mobile 56px.
Gutter (container side padding): desktop 56–60px, tablet 40px, mobile 24px.

---

## 4. Layout & breakpoints

- **Content max-width: 1600px** (hard cap from Tech Direction). Background visuals may bleed full-width beyond.
- **Render range: 390px → 1600px.**
- **Breakpoints (3, each intentionally designed — not compressed desktop):**
  - `mobile`: base, designed at 390px (≤767px)
  - `tablet`: 768px – 1199px
  - `desktop`: ≥1200px
- Grid: 12-col conceptual; hero is split (≈1.05fr / 0.95fr); feature trio = 3-col; updates = 3-col.

---

## 5. Radius, elevation, borders

| Token | Value | Use |
|-------|-------|-----|
| `radius-sm` | 4px | Buttons (comp uses near-square), inputs |
| `radius-md` | 8px | Cards |
| `radius-lg` | 12px | Large panels |
| `radius-pill` | 30px | Pill buttons / eyebrow chips (if used) |

Elevation (restrained): `shadow-sm` 0 1px 3px rgba(10,26,51,.06); `shadow-md` 0 8px 30px rgba(10,26,51,.10);
`shadow-card` 0 12px 40px rgba(10,26,51,.08). Glass card on dark: `rgba(255,255,255,0.06)` bg + `rgba(255,255,255,0.12)` border + blur(8px).

---

## 6. Components & states

### Button
- **Primary:** bg `blue-500`, text white, `radius-sm`, padding 14×28, weight 600, optional right-arrow.
  - hover `blue-400` · active `blue-600` · focus 3px `blue-500 @ 40%` ring · disabled `gray-300` bg / `ink-400` text.
- **Secondary / ghost:** transparent bg, 1px `gray-300` border (or `rgba(255,255,255,.18)` on dark), text `ink-900`/`on-dark`.
  - hover border `blue-500` + text `blue-500`.
- **Text link w/ arrow:** `blue-500`, underline-on-hover, arrow translateX 2px on hover.

### Navigation
Transparent over hero; links `ink-600`/`on-dark-muted` → hover full ink/white; right-side primary "Contact".
Mobile: hamburger → full-screen or slide panel `⚠to design`.

### Eyebrow label
12px uppercase, tracking 0.14em, weight 600, color `blue-500` or `ink-400`.

### Cards
- **Feature (dark trio):** icon (line, blue) + title (h4) + 2–3 line body (`on-dark-muted`).
- **Focus image card:** top image (`radius-md`), title (h4), description (`small`), arrow; subtle hover lift (`shadow-card`, translateY -4px).
- **Leadership card:** headshot (4:5, `radius-md`), name (h4), title (`small`, `ink-400`), prior-company logos row; carousel dots/arrows.
- **Update item:** category eyebrow + date (`small`) + headline (h4) + arrow; divider rule between.

### Stat / metric
Big number (`h2`/`h3`, weight 600/700) + label (`small`, muted). Arranged in bordered row, dividers between.

### Form inputs (Contact)
Input/textarea: `gray-50` bg, 1px `gray-300` border, `radius-sm`, 12×14 padding; focus border `blue-500` + ring.
Label `small` weight 600. Error state border `error` + helper text.

### Section bands
Alternating light (`white`/`gray-50`) and dark (`navy-900`/`navy-800`) full-bleed bands with constrained content. Dark bands carry faint molecular texture.

---

## 7. Motion
Durations: `fast` 200ms, `base` 400ms, `slow` 700ms. Easing: `ease-out` for entrances.
Patterns: fade + 12–20px rise on scroll-in (progressive reveal), soft parallax on helix/molecular bg,
continuous slow helix drift. Honor `prefers-reduced-motion` → disable drift/parallax. Nothing flashy.

---

## 8. Imagery
3D DNA double-helix built from spheres (blue, luminous) on navy; floating molecular node clusters.
Light variant: helix on white with soft blue. Headshots: consistent crop, neutral/dark background.
**All imagery to be delivered by client** (`xenagos/assets/`); use labeled placeholders meanwhile.

---

## 9. Open items feeding this spec
See `knowledge-base/05-open-questions-and-conflicts.md`:
exact font + hex confirmation, logo SVG, real imagery, leadership names (deck vs comp placeholders),
"News" vs "Updates" nav label.
