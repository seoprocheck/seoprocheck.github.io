# AGENTS.md

Guidance for AI coding agents working in this repository.

## Project overview

SEO Pro Check Tools is a collection of free, browser based SEO and GEO tools, published as a static site on GitHub Pages at https://seoprocheck.github.io. There is no backend, no database, no tracking, and no build step. Every tool runs entirely in the visitor's browser.

## Repository layout

- `index.html` at the root is the hub page that links to every tool.
- Each tool lives in its own directory (for example `meta-robots-generator/`) that contains a single self contained `index.html` with its own inline CSS and vanilla JavaScript.
- `README.md` lists every tool with a short description.
- `.nojekyll` disables Jekyll so GitHub Pages serves the files exactly as they are.

## How to run and test

There is nothing to install and nothing to build.

- To preview locally, serve the folder with any static server, for example `python3 -m http.server 8000`, then open `http://localhost:8000/`.
- To test one tool, open its `index.html` directly in a browser and exercise it by hand.
- A tool must keep working with no network connection once the page has loaded. If it needs the internet to function, it does not belong here.

## Conventions (do not break these)

- Zero dependencies. No npm, no package manager, no frameworks, no bundlers, no third party scripts, and no CDN links. Plain HTML, CSS, and vanilla JavaScript only.
- Self contained. Each tool is one `index.html`. Keep its CSS and JavaScript inline or inside that tool's own directory. Do not add shared build tooling.
- Client side only. All processing happens in the browser. Never send user input to a server, an analytics endpoint, or any third party. "No tracking" is a promise to visitors, not a preference.
- Accessible and responsive. Tools should work on mobile and be usable with a keyboard.

## Adding a new tool

1. Create a new directory named after the tool in kebab case.
2. Add a single `index.html` containing the tool, styled and scripted inline, with zero dependencies.
3. Link it from the root `index.html` hub and add a line to `README.md`.
4. Confirm it still works offline after the first load.

## Deployment

The site deploys automatically. Pushing to the `main` branch publishes to https://seoprocheck.github.io through GitHub Pages. There is no CI build to pass, so verify changes in a browser before you push.

## Commit and pull request guidance

- Keep commits small and focused on a single tool or fix.
- Because `main` deploys straight to production, never push a tool in a broken state.
- Write clear commit messages that name the tool touched, for example `meta-robots-generator: fix noindex toggle`.
