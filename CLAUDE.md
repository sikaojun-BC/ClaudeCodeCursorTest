# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a personal project sandbox for building small web games and scripts. Projects are standalone files — no build system, no dependencies, no package manager.

## Running projects

- **HTML games:** `start games/<filename>.html` (opens in default browser on Windows)
- **Python scripts:** `python scripts/<filename>.py`

## Git workflow

**After every meaningful piece of work, commit and push immediately.** This ensures no progress is ever lost and the GitHub repo always reflects the current state.

```bash
git add <specific files>
git commit -m "descriptive message"
git push
```

Commit message rules:
- Use an imperative subject line (e.g. "Add AI opponent to Tic Tac Toe")
- Keep it specific — describe what changed and why, not just "update file"
- Always append: `Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>`

To revert a file to a previous commit:
```bash
git log --oneline          # find the commit hash
git checkout <hash> -- <file>
```

Remote: `https://github.com/sikaojun-BC/ClaudeCodeCursorTest`

## Architecture: games/tictactoe.html

Single-file app — HTML, CSS, and JS all inline. Key design points:

- **State:** `board` (9-element array), `current` (active player), `gameOver`, `scores` (persists across `init()` calls via `scores = scores || ...`)
- **Render cycle:** `init()` → `render()` → DOM is fully rebuilt each click via `boardEl.innerHTML = ''`
- **Win detection:** `checkWin()` iterates the `WINS` constant (8 combos) after every move
- **Color scheme:** dark navy (`#1a1a2e` / `#16213e`), red for X (`#e94560`), blue for O (`#a8d8ea`)
