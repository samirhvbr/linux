# Claude Code configuration — LINUX/KERNEL

Stack: **Kernel scripts / docs**.

## Files
- `settings.json` — the ACTIVE profile (permissions and effort; it chooses no model).
- `settings.local.json` — local override (gitignored), takes precedence over `settings.json`.

## Model
- **This repository does not choose the model.** The model is the user's choice,
  made per session with `/model`, and a subagent inherits the session's model.
  Nothing here pins one: no `model`, no `fallbackModel`, and nothing in `env`
  that steers one — no `ANTHROPIC_MODEL`, no `ANTHROPIC_DEFAULT_*_MODEL`, no
  `CLAUDE_CODE_SUBAGENT_MODEL`. There are no stand-by profiles to copy over
  `settings.json` either; `/model` does that (repodocs ADR-027).
- Effort `max` via the `CLAUDE_CODE_EFFORT_LEVEL` env var (the `effortLevel`
  field only accepts low/medium/high/xhigh).

## Permissions
- `defaultMode: plan`; safety denies (rm -rf, force push, reset --hard, clean -fd, curl|sh).
- **git push allowed** (in `allow`).
