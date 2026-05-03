# importy

[![PyPI Version](https://img.shields.io/pypi/v/importy.svg)](https://pypi.org/project/importy/)
[![Python Versions](https://img.shields.io/pypi/pyversions/importy.svg)](https://pypi.org/project/importy/)
[![License](https://img.shields.io/pypi/l/importy.svg)](https://pypi.org/project/importy/)
[![Status](https://img.shields.io/badge/status-alpha-orange.svg)](https://pypi.org/project/importy/)
[![Open Source](https://img.shields.io/badge/open%20source-yes-brightgreen.svg)](https://github.com/theveryheavy/importy)
[![Downloads (Total)](https://img.shields.io/pepy/dt/importy.svg)](https://pepy.tech/project/importy)
[![GitHub](https://img.shields.io/badge/GitHub-importy-black.svg?logo=github)](https://github.com/theveryheavy/importy)

`importy` is a Python CLI for understanding import relationships, architecture, and startup cost.

It gives you practical answers to questions like:

- "What is my code actually depending on?"
- "Why is this imported?"
- "Can I delete this module safely?"
- "What imports are slowing startup?"

## Features

- Dependency graph mapping
- Circular import detection
- Startup cost analysis
- Lazy import suggestions
- Dead import detection
- Architecture flow visualization
- "Why is this imported?" tracing

## Install

```bash
pip install importy
```

Source code: [github.com/theveryheavy/importy](https://github.com/theveryheavy/importy)

## Command UX

The primary command names are short and memorable:

- `importy map` - dependency map
- `importy loops` - circular imports
- `importy doctor` - health summary
- `importy trace` - why imported / who imports it
- `importy cost` - startup import timing
- `importy lazy` - lazy import suggestions
- `importy dead` - dead import detection
- `importy arch` - architecture flow map

Backward-compatible aliases still work (`graph`, `cycles`, `why`, `time`).

## Quick examples

Map unfamiliar project structure:

```bash
importy map .
```

Inspect cycles:

```bash
importy loops .
```

Trace who imports auth/services/helpers:

```bash
importy trace auth .
importy trace services .
importy trace helpers .
```

Refactoring safety check:

```bash
importy trace helpers.py .
importy dead .
```

Startup import performance:

```bash
importy cost app.py --top 20
```

Architecture view:

```bash
importy arch .
```

Project health (great for onboarding and reviews):

```bash
importy doctor .
```

## Working with monorepos / nested apps

Use `--project-root` when your scan path is inside a larger repo:

```bash
importy map backend/app --project-root backend
importy doctor backend/app --project-root backend
```

## Why this is useful

`importy` is designed for practical engineering work:

1. Onboarding into unfamiliar projects quickly
2. Debugging architecture tangles
3. Refactoring with confidence
4. Reducing startup and cold-start costs
5. Keeping architecture visible as projects grow

## Notes

- Classification (`local`, `third_party`, `stdlib`) depends on the interpreter environment.
- `cost` executes imports for real and requires dependencies installed.
- Dead import detection is static analysis and can have edge cases with dynamic usage patterns.

## Issues & Feedback

Found a bug, incorrect analysis, false positive, or have a feature idea?

Please open an issue on GitHub:

👉 https://github.com/theveryheavy/importy/issues

Good issue reports help improve `importy` much faster. If possible, include:

* Python version
* Operating system
* `importy` version
* Minimal reproducible example
* Expected behavior
* Actual behavior

Feature requests, architecture ideas, and performance suggestions are also welcome.

## Changelog

### 0.1.1

- Renamed and streamlined command UX (`map`, `loops`, `trace`, `cost`, `lazy`, `dead`, `arch`)
- Added architecture flow view and improved tracing output
- Added lazy import suggestions and dead import detection
- Improved startup cost error messaging and table rendering polish

### 0.1.0

- Initial public release with dependency graph, cycle detection, doctor summary, trace/why, and import timing
