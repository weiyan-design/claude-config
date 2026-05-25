---
name: add-design-pattern
description: Add a new visual pattern to Wei's reusable design library at ~/Documents/Vibe Code/_design-library/. Invoke when Wei says "add this to my design library", "save this pattern", "save this as a pattern", "add this to the library", or types `/add-design-pattern`. Walks through the bouncer rule, template fill, README update, and example.html creation in the order Wei established when bootstrapping the library.
---

# Add a Pattern to Wei's Design Library

When this skill is invoked, walk Wei through adding a new visual pattern to
`~/Documents/Vibe Code/_design-library/` following the rules Wei locked in
when bootstrapping the library on 2026-05-24.

The library has strict hygiene rules that prevent it from rotting into a
junk drawer. Enforce them. Don't be a passive scribe — push back when a
pattern fails the bouncer rule, when a section can't be filled, or when the
name is vague.

## Step 0 — Identify the pattern

Before doing anything, confirm what's being added. Look at the recent
conversation context for:
- The source files (HTML / CSS / JS / SVG / assets)
- A working state Wei has approved or settled on
- The project it was built in

If unclear, ask Wei in one sentence: "Which pattern from this session are we
saving — the X, or something else?"

## Step 1 — Apply the bouncer rule

Ask Wei directly: **"Has this pattern been used (or planned for use) in 2+
contexts, or is it unambiguously general?"**

- If Wei isn't sure or admits it's a one-off, push back: explain that
  one-offs stay in the project that birthed them. Suggest waiting for the
  second reuse before extracting. Stop here unless Wei overrides.
- If yes (or Wei overrides), continue.

This single rule is what keeps the library from becoming a junk drawer.
Don't skip it just because Wei is enthusiastic.

## Step 2 — Read the library first

Read `~/Documents/Vibe Code/_design-library/README.md` to:
- See what patterns already exist (avoid duplicates or near-duplicates)
- Understand current naming conventions
- Find an appropriate, non-colliding folder name

If a similar pattern already exists, raise it: "There's already
`<existing-pattern>` that does X. Is this meaningfully different, or should
we update that one instead?"

## Step 3 — Pick a name

The name must be:
- **kebab-case** (e.g. `coverflow-doors-tuner`)
- **describes WHAT it is**, not what it looks like or where it came from
  - Good: `arch-with-animated-wave`, `grain-texture`, `live-tuner-overlay`
  - Bad: `cool-archy-thing`, `wellness-portal-hero`, `experiment-v2`
- **future-proof** — won't conflict with related patterns later

Confirm the name with Wei before creating the folder.

## Step 4 — Scaffold the folder

Create the folder and seed the README from the template:

```bash
mkdir -p "/Users/weiyan/Documents/Vibe Code/_design-library/<pattern-name>"
cp "/Users/weiyan/Documents/Vibe Code/_design-library/_TEMPLATE.md" \
   "/Users/weiyan/Documents/Vibe Code/_design-library/<pattern-name>/README.md"
```

## Step 5 — Fill in every section of the README

Edit the README to fill every section. Pull from conversation context as
much as possible — don't make Wei re-state what was just discussed.

**Frontmatter:**
- `name`: title case
- `status: experiment` (always start here; promote to `production` only on
  the 2nd reuse)
- `added`: today's date (YYYY-MM-DD)
- `last-touched`: same
- `used-in`: list the source project(s) with their status in parens
- `tags`: 3–7 lowercase, comma-separated, useful for filtering

**Required sections (no skipping):**
- **What it does** — one sentence, plain language, what a viewer sees
- **When to use it** — bullets, both ✓ (fits) and ✗ (wrong fits). Be opinionated.
- **What it depends on** — tech stack, browser features, library deps, DOM assumptions
- **How to integrate (3 steps)** — copy-pasteable; lead with the file/snippet to copy
- **Gotchas** — pitfalls *observed during real development* (not theoretical)
- **Locked defaults** — if the pattern has tunable values, enumerate them in a
  table with units and notes. This separates "production-approved settings"
  from "experimentation ranges."
- **Where it came from** — project + date + inspiration sources

**If Wei can't articulate a section, push back.** The library rule is: a
pattern isn't ready to extract if the spec can't be filled. Better to leave
it in the source project than to add a half-documented pattern.

## Step 6 — Create example.html

Build a standalone, runnable demo:
- Single HTML file with inline CSS + JS — no build step, no external deps
  beyond well-known CDNs (Google Fonts, Unsplash placeholders)
- Demonstrates the pattern in isolation, not buried in product chrome
- For interactive/static-comparable patterns, include a toggle so the
  viewer can A/B compare with-pattern vs. without
- Opens by double-clicking in any browser

If the source is already a self-contained HTML file (like Wei's prototypes
often are), simply copy it as `example.html` with minor cleanup if needed.

## Step 7 — Add a row to the top-level README index

Edit `~/Documents/Vibe Code/_design-library/README.md`. In the Patterns
table, add a new row in alphabetical order by name:

```
| [pattern-name](pattern-name/) | experiment | One-line summary | tag1, tag2, tag3 |
```

The one-line summary should be ~10 words and answer "what does this give me
if I drop it in." Same words as the README's "What it does" sentence.

## Step 8 — Tell Wei to record preview.mp4

Conclude by telling Wei to record a short preview:
- For motion patterns: `preview.mp4`, 5–15 seconds, showing the pattern in
  action. macOS: `Cmd+Shift+5` → Record Selected Portion.
- For static patterns: `preview.png` is fine. `Cmd+Shift+4` for selection screenshot.
- For interactive patterns with toggles: a 3-second toggle on/off is enough.

Drop the file in the pattern folder. The README auto-references
`preview.mp4` per the library convention; no README update needed.

You cannot record this yourself — it requires Wei's screen.

## Final confirmation

List all the files created and confirm the pattern is in the library:

```
Created:
  ~/Documents/Vibe Code/_design-library/<pattern-name>/
    ├── README.md
    └── example.html
Updated:
  ~/Documents/Vibe Code/_design-library/README.md  (added row)

To complete: record preview.mp4 and drop in the pattern folder.
```

## Rules to enforce (don't bypass)

1. **The bouncer rule.** No pattern enters without 2+ real or planned uses.
2. **No skipping sections.** If Wei can't fill a section, the pattern isn't ready.
3. **Status starts as `experiment`.** Only promote to `production` after a 2nd successful reuse — not at creation time.
4. **Names describe WHAT, not how it looks.** Push back on vague or cute names.
5. **Don't preemptively extract.** If Wei brings up a pattern that's only been used once, suggest waiting.
6. **No drive-by adds.** Adding is a deliberate ritual; friction here filters junk.

If Wei wants to bypass any of these for a specific add, ask why, and update
the library README rules if the answer suggests a real change in policy.
