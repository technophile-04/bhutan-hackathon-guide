# Blockchain Skills Bootcamp & Hackathon — Briefing Deck

A presentation deck for the **Blockchain Skills Bootcamp & Hackathon 2026**
(Thimphu — by GovTech, sponsored by the Ethereum Foundation).

**Live deck:** https://bhutan-hackathon-guide.vercel.app

It is one self-contained `index.html` file: 13 slides (a cover, a
problem-statement index, 7 problem statements, hackathon rules, what a
winning demo looks like, a resources atlas, and the mentor lineup). It is
designed once at 1920×1080 and auto-scales to any screen or projector.

---

## Presenting it

Open the live link, or run it locally:

```bash
npx serve .
# then open the printed localhost URL
```

Controls while presenting:

- `←` `→` / `PgUp` `PgDn` / `Space` — move between slides
- `Home` / `End` — jump to first / last
- number keys — jump to a slide
- `R` — reset to the first slide
- **Print → Save as PDF** — produces a clean one-slide-per-page PDF to hand out

---

## Reusing it next year — the easy way

You do **not** need to know HTML. The fastest way to produce next year's
deck is to let [Claude Code](https://www.anthropic.com/claude-code) do it,
guided by the playbook prompt below.

**Steps:**

1. Install Claude Code (one-time): https://www.anthropic.com/claude-code
2. Open a terminal in an empty folder and run `claude`.
3. Copy the **entire** prompt in the grey box below.
4. Paste it into Claude Code and press enter.
5. Answer its questions one at a time — it will ask you for the new
   event name, dates, problem statements, rules, mentors, and so on.
6. When it finishes it will publish the new deck and give you the live link.

Claude Code reads this repository first, so it already understands how the
deck is built and what the rules are. You only provide the new content.

### The playbook prompt — copy everything between the lines

> ⚠️ **If you forked this into your own GitHub account/org, replace the
> repository URL on the first line of the prompt below with your fork's
> URL** — otherwise Claude Code edits a copy you can't publish to.

```text
You are updating a presentation deck for a government hackathon. The deck
lives in this GitHub repository:

  https://github.com/technophile-04/bhutan-hackathon-guide

TASK
Clone that repository (git clone the URL into the current folder, then cd
into it). Read these files completely before doing anything else:
  - index.html  (the entire deck — one file, all 13 slides + CSS + scripts)
  - deck-stage.js  (the web component that powers navigation/scaling — do
    not modify this file)
  - README.md  (this playbook and the conventions section at the bottom)

Then help me produce an updated deck for a NEW event by interviewing me
and editing index.html. Do not summarise or rewrite my content. Keep the
visual design exactly as it is — you are swapping content and branding,
not redesigning.

HOW TO INTERVIEW ME
Ask about ONE topic at a time, show me what you are going to change, and
wait for my answer before moving on. If I say "no change" or "keep it",
leave that part exactly as it is. Go through these topics in order:

  1. Event identity — event name, one-line tagline, city/location,
     dates, the submission deadline, the organising body, and the
     sponsor. (These appear on the cover slide, the browser title, and
     the vertical "spine" label that runs up the left edge of every
     slide.)

  2. Problem statements — I will paste the full text of each problem
     statement. Reproduce it WORD FOR WORD. Do not shorten, paraphrase,
     re-order, or "clean up" the wording. Preserve the original
     capitalisation, numbers, punctuation, curly quotes/apostrophes,
     dashes, and any italic emphasis exactly as I give them. Also ask me
     for a short title for each one (used only on the index slide).

  3. Hackathon rules — the numbered list of rules and the closing line.

  4. Winning demo — the guidance points for what makes a good demo.

  5. Resources — the bookmarkable links, grouped into sections.

  6. Mentors — for each mentor: name, their skills, and whether they
     should be visually flagged. A mentor can be a normal mentor, a
     "problem-statement specialist" (saffron flag), part of a named team
     (jade flag), or a solo person from a partner org (sky-blue flag).
     Ask which, and what the flag label should say.

RULES YOU MUST FOLLOW (this deck has hard constraints)

  - Fixed canvas. Every slide is exactly 1920×1080 and does not scroll.
    Content must fit. If a problem statement is long, it uses a
    two-column layout (the "ps-body" style; add the "dense" class for
    the longest ones). If something still overflows the bottom red rule,
    split it across two slides titled "... · 1/2" and "... · 2/2" — do
    NOT cut the text.

  - Verbatim problem statements. The deck chrome (titles, labels) is
    intentionally all-lowercase by design. The problem statements are
    the exception: they sit in a block with text-transform:none and must
    appear EXACTLY as written. Never lowercase, summarise, or restyle the
    words of a problem statement.

  - Page numbers are automatic. A script at the bottom of index.html
    numbers the slides from their order in the file. Never hand-type a
    page number. A new numbered slide just needs an empty
    <div class="pagenum"></div>. The cover slide has the attribute
    data-cover so the script skips it (cover gets no number).

  - The spine label (the vertical text on every slide) must stay short
    because it runs vertically — keep it roughly the length of the
    current one.

  - Mentor flags. The colour system already exists in the CSS:
    default = monastic red, mentor-card--focused = saffron (problem
    specialist), mentor-card--team-ndi = jade (a team),
    mentor-card--from-govtech = sky (solo org). To add a new
    organisation flag, clone that 3-line CSS pattern with a new colour
    from the palette and a new class name.

  - The cover slide is the reusable title card. Swap its title,
    subtitle, eyebrow (the credits line) and the meta line
    (location / date / deadline). If the new event name is long, reduce
    the cover title font-size so it fits on a few lines.

  - Do not open the deck in a browser or take screenshots to "check" it.
    Reason from the HTML/CSS directly. Everything you need (sizes,
    colours, layout) is in the source.

WHEN DONE
  - Sanity check: the number of "<section" opening tags must equal the
    number of "</section>" closing tags.
  - Run: git add -A && git commit && git push
  - The repository is connected to Vercel, so pushing automatically
    publishes the new deck. Tell me the live URL and a short summary of
    what changed. If the push fails because this is a fresh copy with no
    Vercel link yet, tell me and walk me through running the Vercel CLI
    (`npx vercel` then `npx vercel git connect`).
```

---

## Reusing it manually (if you'd rather edit it yourself)

Everything is in `index.html`. Each slide is one `<section>` element
inside `<deck-stage>`. To add a slide, copy an existing `<section>`,
change its content, and leave a `<div class="pagenum"></div>` in it —
the numbering script does the rest. The cover slide carries `data-cover`
so it is skipped by numbering.

Push to the `master` branch and Vercel redeploys automatically. If you
forked this into a brand-new repository, link it once with
`npx vercel` and `npx vercel git connect`.

---

## Conventions cheat-sheet

These are the rules baked into the deck. The playbook prompt repeats
them so Claude Code follows them, but they are here for humans too.

| Area | Rule |
|---|---|
| **Canvas** | Fixed 1920×1080, no scrolling. Content must fit. Long text → two columns (`ps-body`, add `dense`). Still overflowing → split into `· 1/2` and `· 2/2` slides, never cut. |
| **Lowercase** | All chrome is lowercase by design (`text-transform: lowercase` on `section`). |
| **Verbatim** | Problem statements use `ps-body` with `text-transform: none`. Reproduce them exactly — wording, case, punctuation, curly quotes, italics. Never summarise. |
| **Numbering** | Auto-generated from slide order by a script at the bottom of the file. Never hand-number. Cover uses `data-cover` to be skipped. |
| **Spine** | The vertical label on every slide carries the event name; keep it short. |
| **Mentor flags** | `--focused` = saffron (problem specialist), `--team-ndi` = jade (team), `--from-govtech` = sky (solo org). Clone the 3-line CSS pattern for new orgs. |
| **Cover** | The reusable title card (`data-cover`). Swap title / subtitle / eyebrow / meta. Shrink the title font for longer event names. |
| **Deploy** | Push to `master` → Vercel auto-publishes. Fresh fork → `npx vercel` + `npx vercel git connect` once. |

## Design source

Originally authored at [claude.ai/design](https://claude.ai/design) and
exported as static HTML/CSS/JS. The `<deck-stage>` web component
(`deck-stage.js`) handles keyboard navigation, auto-scaling, the
thumbnail rail, and print-to-PDF. Do not modify `deck-stage.js`.

---

> ⚠️ **Forked this?** Before using the playbook prompt, replace the
> repository URL on its first line with your own fork's URL — otherwise
> Claude Code edits a copy you can't publish to.
