## Purpose

Make an AI coding assistant immediately productive in this repository by describing the project's structure, developer workflows, integration points, and safe editing rules. Only document patterns discovered in the repo (no aspirational practices).

## Big-picture architecture (what I observed)

- This is mostly a static site project in `frontend/` (HTML/CSS/JS). The root and `backend/`, `backend/api/`, and `backend/tests/` folders exist but currently contain placeholder READMEs.
- No package manifests (no `package.json`, `requirements.txt`, etc.) and no CI config under `.github/` were found.

## Key files and where to look

- `frontend/index.html` — primary HTML; includes links to `css/` and `js/` files and external CDNs (jQuery/Google). Example signal: the counter element with id `counter` is updated via JS.
- `frontend/css/` — theme and layout styles (default.css, layout.css, media-queries.css, magnific-popup.css).
- `frontend/js/` — client scripts (init.js, jquery-*.js, plugins). `init.js` and `main.js` are good places to modify dynamic behavior.
- `frontend/images/` — images (update profile pic at `images/me.png`).
- `frontend/font-awesome/` and `fontello/` — local icon assets and fonts used by the template.
- `backend/`, `backend/api/`, `backend/tests/` — currently placeholders. Treat these as separate areas if you add server code or tests; create a top-level README update when adding build/test tooling.

## Developer workflows (discovered / recommended minimal commands)

- Local preview (no build tool present):

  - Serve the `frontend/` folder with a simple HTTP server: `cd frontend && python3 -m http.server 8000` and open `http://localhost:8000`.
  - Alternatively open `frontend/index.html` in a browser for static inspection, but some JS features may require being served (CORS/paths).

- There is no CI or test runner configured. If you add tests or a build tool, update the appropriate README and add a manifest (`package.json`, `requirements.txt`, etc.).

## Project-specific conventions and patterns

- This repo uses a prebuilt HTML template (CeeVee) with classic directories (`css/`, `js/`, `images/`). Keep relative paths intact when editing assets.
- JS relies on jQuery and several plugin scripts (magnific-popup, flexslider). Avoid converting to a different runtime/framework without adding package manifests and documentation.
- Social links and external references (GitHub, YouTube, Twitter) are embedded directly in the template — changing them is a common low-risk edit.

## Integration points & external dependencies

- External CDNs used in `frontend/index.html` (Google-hosted jQuery). If you change these, ensure fallback copies in `frontend/js/` remain available.
- Font files exist under `frontend/font-*` folders; changes to icons or fonts must preserve relative paths.

## Guidance for AI edits (do this, not that)

- Be conservative: do small, reversible edits and prefer updating the HTML/CSS/JS in `frontend/` unless a clear backend API exists.
- If you introduce a build system or runtime dependency (npm, pip), add a manifest (`package.json`, `requirements.txt`) and update `backend/README.md` or `frontend/README.md` to document install/run commands.
- When modifying dynamic behavior, update `frontend/js/init.js` (or `main.js`) and keep changes isolated. Use the `counter` element and `init.js` as examples of where behaviour lives.
- When adding tests, place them under `backend/tests/` and update `backend/tests/README.md` with the test command and any environment requirements.

## What to update in repo when making changes

- Any new tooling or CI must include: manifest (package.json/requirements.txt), updated README in the relevant folder, and optional `.github/workflows/` CI files.
- Add a short changelog entry to the root `README.md` if making non-trivial changes (new runtime, deploy steps).

## Where to ask the human

- If you need to add a runtime (Node, Python, .NET) or scaffold a backend API, ask what runtime/version the maintainer prefers before creating manifests.
- If you plan to remove or replace third-party assets (fonts, jQuery), ask whether bundling or CDN usage is preferred.

---
If anything here is unclear or you want the instructions to be stricter/looser (for example: allow creating a Node toolchain), tell me which parts to change and I will iterate.
