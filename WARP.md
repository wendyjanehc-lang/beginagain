# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project overview

This repository is a minimal static site consisting of a primary HTML entrypoint with inline styles, plus an experimental animated variant:

- `index.html` – root HTML document that defines the entire page markup, CSS, and animated "LISTEN closely" text sequence that ends with **I am making all things NEW!**.
- `my-animation/` – holds an alternate entrypoint (`index.html`) and shared styles/assets for iterating on the animation.
- `Elements/` – contains the `manic_emphasis-03.png` underline graphic used to emphasize the word "all" in the final line.
- No build tooling, package manager configuration, or test framework is currently defined.

The page is self-contained and uses:
- A Google Fonts stylesheet for the `Homemade Apple` font.
- Inline CSS in a `<style>` block for layout and typography.
- A simple semantic structure: `body` → `main.hero` → `h1.hero-title`.

## Commands and workflows

Because there is no build system, everything runs directly in the browser.

### Previewing the site locally

Open `index.html` directly in a browser, or serve the directory with a simple static server, for example:

```bash
open index.html
```

or, using Python’s built-in HTTP server from the project root:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/index.html` in a browser.

### Dependencies, build, lint, and tests

- There are no declared runtime or development dependencies in this repo.
- No build step is required; `index.html` is the source of truth.
- No linting or formatting tools are configured.
- No automated tests or test runners are configured.

If you introduce tooling (e.g., a package manager, bundler, linter, or tests), update this section with the canonical commands (install, build, lint, test, and how to run a single test).

## Code structure and extension points

High-level structure of `index.html`:

- **Global reset**: `*`, `*::before`, `*::after` reset margins, paddings, and set `box-sizing: border-box`.
- **Layout**: `body` is a full-viewport flex container centering content both horizontally and vertically.
- **Hero container**: `.hero` wraps the main content and handles padding and text centering.
- **Typography**: `.hero-title` applies the script-style Google Font and uses `clamp` for responsive font sizing and `letter-spacing` for a spaced-out, uppercase look.

When extending the page:

- Keep the hero structure (`main.hero` and `.hero-title`) consistent if you want to preserve the current aesthetic.
- Consider extracting the inline `<style>` block into a separate CSS file (e.g., `styles.css`) if styles become more complex.
- If you add JavaScript or additional pages, document the new entrypoints and any new commands here for future agents.
