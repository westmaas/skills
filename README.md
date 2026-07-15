# skills

Agent skills for [Claude Code](https://claude.com/claude-code). Each top-level
directory is a self-contained skill: a `SKILL.md` (with YAML frontmatter Claude
reads to decide when to use it) plus any supporting `references/`.

## Install

Copy a skill into your personal skills directory:

```bash
git clone https://github.com/westmaas/skills.git
cp -R skills/design-crawl ~/.claude/skills/
```

Claude Code discovers it automatically on the next session — invoke it by name
(`/design-crawl`) or just describe the task and let Claude match it.

## Skills

### [`design-crawl`](./design-crawl)

Explore any web app in a real browser, capture a multi-viewport screenshot
crawl, and surface UX/interaction inconsistencies **by observation** — not
against a fixed checklist. It:

- walks the app per persona in an isolated browser session (auth-aware, with the
  Chrome-CDP and SSO gotchas already handled),
- packages screenshots + a machine-readable `manifest.json` + a human `README`
  into a zip,
- builds an **interactive crawl visualizer** (`crawl-visualizer.html`) where you
  mark each screen **Keep / Redesign / Not sure** with free-text direction, and
- generates a **Claude Design handoff prompt** carrying the crawl evidence and
  your per-screen feedback.

Exploration-first and app-agnostic: personas, flows, and constraints are inputs,
never assumptions, and it doesn't seed the walk with predetermined conclusions.

---

Requires the `agent-browser` CLI for the crawl step
(`npm i -g agent-browser && agent-browser install`).
