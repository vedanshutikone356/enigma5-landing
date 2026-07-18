# prompts.md — Enigma 5.0 Landing Page

Documenting the key prompts and creative decisions used while building this project with Claude (Anthropic).

---

## Prompt 1 — Creative Direction & Visual Theme

> "I need to build a hackathon landing page for 'Enigma 5.0'. The word Enigma should drive the entire visual identity. Don't give me a generic tech template. Give me a design plan first — palette, typefaces, layout concept, and a single signature element that will make this page feel unique."

**What this achieved:** Instead of jumping to code, this forced a design-first approach. The AI proposed interpreting Enigma as a cipher/classified-document aesthetic — dark void background, violet and terminal-green accents, monospace typography, and a glitch decode animation as the signature element.

---

## Prompt 2 — Typography & Palette Specification

> "Use Space Grotesk as the display and body typeface for its geometric-techy feel, paired with JetBrains Mono for data labels, eyebrows, and nav items. Set the palette as: #0A0A0F (void black), #7C3AED (cipher violet), #10B981 (terminal green), #F8FAFC (ghost white), #1E1E2E (card surface). Every color decision must come from this token system — no deviations."

**What this achieved:** Locked the token system so the AI couldn't drift into generic gradients or off-brand colors mid-generation. Treating the palette as a strict constraint produced consistent results across all components.

---

## Prompt 3 — Hero Section & Signature Animation

> "Build the hero section with a cipher-decode animation on the word ENIGMA — on page load, each letter should cycle through random alphanumeric characters before resolving to the correct letter, staggered left to right so it feels like cracking a code. No libraries — pure requestAnimationFrame. Also add a horizontally scrolling tape of hex codes and binary strings at the bottom of the hero, like a terminal output."

**What this achieved:** This produced the page's most distinctive moment. The staggered decode effect creates immediate atmosphere and communicates the Enigma theme kinetically rather than just visually.

---

## Prompt 4 — Layout Architecture & Section Order

> "Structure the page in this order: fixed nav → hero (full viewport) → stats bar (4-column grid) → tracks (2-column cards) → timeline (left-ruled list, not numbered) → prize (single centered box) → register (centered CTA) → contact (2-column cards) → footer. Every section should be separated by a 1px border in #2A2A3A, no heavy dividers or decorative elements."

**What this achieved:** Defined a clear information hierarchy that flows from context → details → action. The border-as-separator approach keeps the page feeling structured without decorative clutter.

---

## Prompt 5 — Mobile Responsiveness Rules

> "Make the layout fully responsive. On mobile: hide the nav links (keep only logo and Register CTA), collapse the 4-column stats bar to 2×2, collapse all 2-column grids to 1 column, reduce section padding to 4rem 1.25rem, and make the hero headline scale with clamp(3.5rem, 10vw, 8rem). Respect prefers-reduced-motion — disable the cipher tape scroll and glitch effects for users who have it enabled."

**What this achieved:** Separated the responsive logic as its own prompt pass, which produced cleaner media query output. Explicitly requesting `prefers-reduced-motion` support ensured accessibility wasn't an afterthought.

---

## Prompt 6 — Scroll Reveal Micro-interactions

> "Add a lightweight IntersectionObserver fade-up on scroll for track cards, timeline items, contact cards, and the prize box. No libraries. Start opacity at 0 and translateY(24px), transition to opacity 1 and translateY(0) on intersection. Threshold 0.1. Keep the transition duration at 0.5s — fast enough to feel snappy, slow enough to register."

**What this achieved:** Added polish without performance cost. Using IntersectionObserver over scroll event listeners keeps the animation work off the main thread and avoids jank.

---

## Prompt 7 — Copy & Microcopy Direction

> "Write all the page copy in a terse, atmospheric style — short declarative sentences, no filler marketing language, nothing that sounds like a default tech template. The headline for the Register section should be a command that ties back to the Enigma theme. Timeline event names should feel like classified milestones, not calendar entries."

**What this achieved:** The copy ended up matching the design's atmosphere. Lines like 'The cipher drops. Read carefully — every word is deliberate.' and 'Glory is infinite. Cash is finite. Both are real.' feel authored rather than generated.

---

## Key Design Decisions (Director's Notes)

- **No hero background image or video** — the radial violet glow is the only ambient element, keeping load times fast and the page clean
- **Left-ruled timeline** — chose a ruled list over numbered steps because the timeline isn't a process the user follows, it's a sequence they observe
- **Stats bar as a divider** — the 4-up stat strip between hero and content acts as a visual breath and front-loads the key facts (prize, tracks, team size)
- **Single glitch signature** — the glitch CSS on the hero title activates every 6 seconds, creating atmosphere without being distracting to readers who've already seen it once

---

*Built with Claude (Anthropic) as an AI assistant. All creative direction, layout decisions, copy writing, and structural choices were made by the developer. The AI was used to accelerate implementation, not replace judgment.*
