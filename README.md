# Frontend Design — With-Skill vs Without-Skill

Six single-file landing pages. Three design briefs, each built twice: once with a
design skill guiding the generation, once without it.

The point is not that any one page is the best it could be. The point is what
changes between the two columns when the only variable is the guidance.

`COM` and `SEM` are Portuguese for *with* and *without*.

---

## The pages

| Brief | Subject | With skill | Without skill |
|---|---|---|---|
| 1 | **Portfolio** — an independent interface designer | [`1-portfolio-COM-skill.html`](1-portfolio-COM-skill.html) | [`1-portfolio-SEM-skill.html`](1-portfolio-SEM-skill.html) |
| 2 | **Marrow** — a two-person speciality coffee roastery in Porto | [`2-marrow-COM-skill.html`](2-marrow-COM-skill.html) | [`2-marrow-SEM-skill.html`](2-marrow-SEM-skill.html) |
| 3 | **Hearth** — a generative audio engine | [`3-hearth-COM-skill.html`](3-hearth-COM-skill.html) | [`3-hearth-SEM-skill.html`](3-hearth-SEM-skill.html) |

Every page is one self-contained `.html` file — markup, tokens, styles and
behaviour in a single document. No build step, no package manager, no server.

---

## What actually differed

Measured across the six files:

| File | Size | Lines | CDN deps | Libraries |
|---|---|---|---|---|
| `1-portfolio-COM-skill` | 49.4 KB | 1073 | 8 | Three.js, GSAP, Lenis |
| `1-portfolio-SEM-skill` | 71.0 KB | 1457 | 3 | Three.js, GSAP |
| `2-marrow-COM-skill` | 49.6 KB | 1244 | 5 | GSAP, Lenis |
| `2-marrow-SEM-skill` | 63.4 KB | 1446 | 0 | — |
| `3-hearth-COM-skill` | 34.0 KB | 822 | 7 | Three.js, GSAP, Lenis |
| `3-hearth-SEM-skill` | 44.2 KB | 1176 | 0 | Web Audio API |

Two patterns hold across all three briefs:

- **The guided pages are smaller.** Every `COM` file is 22–30% shorter than its
  `SEM` counterpart for the same brief. Less hand-rolled scaffolding.
- **The guided pages lean on libraries; the unguided ones reinvent.** `COM`
  reaches for GSAP and Lenis for motion and smooth scroll. `SEM` writes its own
  — `2-marrow-SEM` and `3-hearth-SEM` ship with zero external dependencies and
  pay for it in volume.

Which trade you prefer is the interesting question. Fewer dependencies is a real
virtue; so is not rewriting an easing library. The comparison is here to be
looked at, not to declare a winner.

---

## Shared ground

Both columns converged on the same broad house style, which suggests it comes
from the briefs rather than the guidance:

- Design tokens declared as CSS custom properties in a `:root` block
- Warm paper-and-ink palettes with a single hot accent (`#FF4A1C` recurs)
- Fluid type scales built on `clamp()`
- Variable fonts from Google Fonts — Fraunces, Instrument Serif, Inter Tight,
  Bricolage Grotesque, DM Mono
- Full `<meta>` and Open Graph blocks, inline SVG data-URI favicons

---

## Running them

Open any file directly in a browser:

```bash
start 1-portfolio-COM-skill.html
```

The pages fetch fonts and libraries from CDNs, so a network connection is needed
for the full effect. `2-marrow-SEM-skill.html` and `3-hearth-SEM-skill.html` have
no CDN dependencies at all beyond fonts.

To serve the whole set over HTTP instead:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

---

## Stack

Plain HTML, CSS and JavaScript. Where libraries appear they are pulled from
jsDelivr at fixed versions:

- [Three.js](https://threejs.org/) `0.185.1` — WebGL scenes
- [GSAP](https://gsap.com/) `3.15.0` — animation, `ScrollTrigger`, `SplitText`, `CustomEase`
- [Lenis](https://lenis.darkroom.engineering/) `1.3.26` — smooth scrolling
- Web Audio API — used directly in `3-hearth-SEM-skill.html`

---

## License

[MIT](LICENSE) © 2026 Tomás Girão

The pages describe fictional people and businesses. Noor Abadi, Solenne Riva,
Marrow and Hearth were invented for the briefs and are not real.
