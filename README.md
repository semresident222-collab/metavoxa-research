# MetaVoxa Research

**research.metavoxa.com** — Where observation becomes evidence.

> MetaVoxa Research investigates the distance between lived reality and institutional recognition across culture, gender, and systems — producing rigorous evidence that informs policy, practice, and public understanding. This repo holds the public-facing site for that evidence layer.

---

## What This Is

MetaVoxa Research is the credibility layer of the MetaVoxa ecosystem. Where Press builds language and Labs builds instruments, Research builds the evidence that institutions are required to respond to. The site is a public-facing index of active investigations, publications, preprints, and research programs — with abstracts and key findings hosted directly, and full papers linking out to their institutional homes (ORCID, Zenodo, The Lancet).

---

## The Three Content Sections

### Active Investigations
Five ongoing research streams. Each has a code (INV-001 through INV-005), a status badge, a brief summary on the dashboard card, and a full detail modal (abstract, key findings, related work, external links).

| Code | Title | Status | Area |
|------|-------|--------|------|
| INV-001 | Diagnostic Delay in Neurodivergent Women | ONGOING | Neurodivergence · Diagnosis |
| INV-002 | Cultural Non-Recognition Mechanisms | IN PROGRESS | Systems · Culture |
| INV-003 | Masking Load as a Measurable Burden | ONGOING | Neurodivergence · Measurement |
| INV-004 | Migration as a Diagnostic Variable | IN PROGRESS | Medicine · Systems |
| INV-005 | Functional Pain & Clinical Misreading | ONGOING | Medicine · Selfhood |

### Recent Publications
Four published outputs. Links out to ORCID, Zenodo, and The Lancet Psychiatry. Full abstracts and key findings hosted on this page.

| Code | Title | Type | Status |
|------|-------|------|--------|
| PUB-001 | The Lancet Psychiatry Collaboration | Peer-Reviewed | Published 2025 |
| PUB-002 | ADHD Digital Biomarker — Feasibility Protocol | Preprint | Published 2026 |
| PUB-003 | KEYNOTE-991 Protocol Review | Peer-Reviewed | Published 2025 |
| PUB-004 | Aduhelm Efficacy Analysis | Preprint | Published 2025 |

### Research Programs
Three multi-year institutional programs.

| Code | Title | Type | Status |
|------|-------|------|--------|
| PROG-001 | Dr. med. Research Program | Doctoral Research | Protocol Stage |
| PROG-002 | Charité Collaboration | Institutional Collaboration | Active |
| PROG-003 | ACRP 2027 Submissions | Conference Submissions | Submitted |

---

## Modal System

Every dashboard card is clickable. Clicking opens a modal overlay with:
- Full abstract
- Key findings (bulleted)
- Related work (linked to Labs frameworks, Press essays, Strategic Questions Registry entries)
- External links (ORCID, Zenodo, Lancet, institutional pages)

Click outside the modal, click the × button, or press Escape to close.

This pattern keeps the dashboard scannable while ensuring full research detail is always one click away — without requiring a separate page per entry.

---

## Academic Profile Section

Four credential cards, each with a copper top-border:

| Credential | Detail |
|-----------|--------|
| ORCID | 0000-0003-4152-3863 — persistent identifier across all published outputs |
| Charité Berlin | Final-year MD candidate · Dr. med. research program active |
| ICH-GCP Certification | Good Clinical Practice · Clinical trial operations · Vivantes Hospital Berlin |
| GitHub | Martha-Wuya-Koroma — technical research and data analysis repositories |

Institutional collaborations row below: Charité · ORCID · ResearchGate · Zenodo · More Partners

---

## File Structure

```
research.metavoxa.com/
├── research.html           — Main page (rename to index.html when deploying)
└── research-board.jpg      — Hero image (investigation corkboard scene)
```

**Note:** The file is named `research.html` in this repo. Rename to `index.html` at the root of the `research.metavoxa.com` deployment.

---

## Image Asset

| File | Description | Used in |
|------|-------------|---------|
| `research-board.jpg` | Detective-style investigation corkboard — post-it notes, string connections, world map, handwritten field notes, warm amber light on dark background. Wide landscape. | Hero section — full-width background |

The hero degrades gracefully if the image is absent — falls back to a dark gradient. Nothing breaks.

---

## Navigation

The nav has six anchor links that smooth-scroll to sections on the same page:

| Link | Section |
|------|---------|
| OVERVIEW | Hero |
| INVESTIGATIONS | Dashboard — Investigations column |
| PROGRAMS | Dashboard — Programs column |
| PUBLICATIONS | Dashboard — Publications column |
| COLLABORATIONS | Academic Profile section |
| EVIDENCE ARCHIVE | Archive CTA section |

Active nav highlighting updates as you scroll. On mobile, links collapse into a hamburger drawer.

**Ecosystem dropdown:** Top-right "PART OF THE METAVOXA ECOSYSTEM ▾" opens a panel showing Research, Labs, and Press as siblings — each with a brief descriptor and link. Consistent with the ecosystem panel in the Research hero.

---

## Light/Dark Toggle

The toggle is in the top-right nav. The page defaults to dark mode. Light mode switches the page body, cards, and content sections to a warm cream/white palette. The nav stays dark regardless of mode — it is a fixed black frame around the content.

CSS is fully variable-driven. Both themes are defined in `:root[data-theme="dark"]` and `:root[data-theme="light"]` at the top of the stylesheet. Adding new elements: use CSS variables (`--bg`, `--surface`, `--text`, `--copper`, etc.) and they inherit both themes automatically.

---

## Responsive Breakpoints

| Breakpoint | Layout |
|-----------|--------|
| > 1100px (desktop) | Three-column dashboard · Split hero with image and ecosystem panel |
| 769–1100px (tablet) | Two-column dashboard · Hero collapses to text only · Ecosystem panel hidden |
| ≤ 768px (mobile) | Single column · Hamburger nav · Stats in 2×2 grid · All sections stacked |

---

## To Add a New Entry

**New investigation or publication:**
Append a new object to the relevant array (`INVESTIGATIONS`, `PUBLICATIONS`, or `PROGRAMS`) in the `<script>` section at the bottom of the HTML file. The dashboard renders from the data — no HTML editing needed.

Required fields for each entry:
```javascript
{
  id: "2026",               // display date or short identifier
  code: "INV-006",          // unique code
  type: "INVESTIGATION",    // type label shown on card
  statusClass: "s-ongoing", // CSS class for badge colour
  statusLabel: "ONGOING",   // text shown in badge
  area: "AREA · SUBAREA",   // shown below code on card
  title: "...",             // card and modal headline
  desc: "...",              // short card description (1–2 sentences)
  team: "Lead · MWK",       // shown in card footer
  abstract: "...",          // full abstract in modal
  findings: ["...", "..."], // bulleted key findings in modal
  related: ["..."],         // related work tags in modal
  links: [                  // external links in modal (empty array if none)
    { label: "VIEW ON ZENODO →", url: "https://zenodo.org" },
    { label: "RELATED ESSAY →", url: "...", muted: true }
  ]
}
```

**Status badge classes available:**
`s-ongoing` · `s-progress` · `s-published` · `s-preprint` · `s-submitted` · `s-protocol` · `s-active`

---

## Content Source of Truth

All content derives from the **MetaVoxa Knowledge Core** — specifically:

- **Research Library** (Section 6) → all publication and protocol entries
- **Strategic Questions Registry** → investigation research questions and related entries
- **Founder Profile** → academic credentials, affiliations, certifications
- **Innovation Registry** → cross-references to Labs frameworks (Digital Biomarker, MLI)

**The Fortress Principle applies:** if content here and the Knowledge Core disagree, the Knowledge Core wins. Update the Core first, then update the site.

---

## Ecosystem Position

```
metavoxa.com  (neutral landing — front door)
   ├── atrium.metavoxa.com   — sovereign digital estate
   ├── labs.metavoxa.com     — research infrastructure and frameworks
   ├── press.metavoxa.com    — public voice, essays, vocabulary
   ├── research.metavoxa.com — THIS REPO — evidence and publications
   └── marthakoroma.com      — founder threshold (external)
```

Research is distinct from Labs (which builds instruments) and Press (which builds language). Research converts observation into evidence — the form institutions are required to respond to.

---

*Maintained by Martha Wuya Koroma. Part of the MetaVoxa Knowledge Core ecosystem.*
*Last updated: June 2026*
