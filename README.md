# RepoLens

Paste any public GitHub repository and get a code health report in seconds: a 0-100 score, language breakdown, commit activity, a treemap of where the code weighs most, plain-language findings, and a searchable file explorer.

Runs entirely in the browser. No backend, no build step, no API key.

## What it does

- **Live analysis** through the GitHub REST API: repository metadata, languages, the full file tree and weekly commit activity. Source code is never downloaded, only the tree.
- **Health score** across five weighted checks: structure (20%), documentation (20%), testing (25%), maintainability (20%) and activity (15%).
- **Findings** written from the signals: strengths, risks and suggested next steps.
- **Treemap** of the largest source and test files, grouped by top-level folder, laid out with a squarified treemap algorithm.
- **File explorer** with text search and a file-type filter.
- **Shareable links** in the form `?repo=owner/name`.
- **Sample projects** bundled in the page, so it works offline and demos instantly.
- Light and dark themes, responsive down to phone width.

## Run it

Open `index.html` in a browser, or on Replit:

1. Create a new Repl and choose the **HTML, CSS, JS** template (or upload this folder).
2. Replace the default `index.html` with this one and press **Run**.
3. To publish, use **Deploy** and pick a **Static** deployment.

GitHub allows 60 unauthenticated API requests per hour per visitor. One analysis uses about 4 requests, and the page shows how many are left.

## How the scoring works

| Check | Weight | Signals |
| --- | --- | --- |
| Structure | 20% | files in root, folder count, depth, manifest, .gitignore, code concentration |
| Documentation | 20% | README size, LICENSE, docs folder, CONTRIBUTING, CHANGELOG |
| Testing | 25% | test files as a share of source files, CI configuration |
| Maintainability | 20% | files over 30 KB, CI, linter config, lock file |
| Activity | 15% | time since last push, active weeks in the last 26 |

These are heuristics from file names, sizes and commit counts. They are a fast first read, not a code review.

## Tech

Plain HTML, CSS and JavaScript. No frameworks or dependencies. Scoring and layout logic are pure functions, separate from the UI code.

## Ideas for extending it

- Add a GitHub token field to raise the rate limit to 5,000 requests per hour.
- Compare two repositories side by side.
- Add a small backend that embeds code chunks and answers questions about the codebase with file citations.
- Export the report as a PDF.
