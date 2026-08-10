# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

Personal documents repository. Currently contains a CV (`cv/`) built with LaTeX on the [Awesome-CV](https://github.com/posquit0/Awesome-CV) template (`awesome-cv.cls`, CC BY-SA 4.0).

## Build

Compile from inside `cv/` (the `.tex` files use paths relative to that directory):

```bash
cd cv && lualatex cv.tex
```

The last successful build used LuaLaTeX (TeX Live 2026). XeLaTeX also works — the class only requires a fontspec-capable engine; plain `pdflatex` will not work. Output is `cv/cv.pdf`; `cv.aux` and `cv.log` are build artifacts.

## Structure

- `cv/cv.tex` — entry point: document config (colors, margins, personal info in the header) and the ordered list of `\input{lib/...}` section includes.
- `cv/lib/*.tex` — one file per CV section (education, skills, experience, honors, etc.). Content edits happen here; to add/remove/reorder sections, edit the `\input` list at the bottom of `cv.tex`.
- `cv/awesome-cv.cls` — the template class. Prefer configuring via the hooks exposed in `cv.tex` (e.g. `\colorlet{awesome}{...}`, `\setbool{acvSectionColorHighlight}`) over editing the class directly.
