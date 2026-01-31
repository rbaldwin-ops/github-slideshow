# CLAUDE.md - AI Assistant Guide for github-slideshow

## Project Overview

This is a **Jekyll-based presentation slideshow** repository built with reveal.js. It serves as a GitHub Learning Lab training template for teaching Git and GitHub through interactive slide presentations.

**Tech Stack:**
- Jekyll 3.9.0 (Ruby static site generator)
- reveal.js 3.9.2 (JavaScript presentation framework)
- Markdown for content
- GitHub Pages for hosting

## Repository Structure

```
/
├── _includes/              # Reusable HTML snippets
│   ├── head.html          # Meta tags, CSS links, script setup
│   ├── script.html        # Reveal.js initialization
│   └── slide.html         # Individual slide template
├── _layouts/               # Jekyll layout templates
│   ├── presentation.html  # Main presentation layout
│   ├── slide.html         # Slide wrapper layout
│   └── print.html         # Print layout variant
├── _posts/                 # Markdown slide content (YYYY-MM-DD-title.md)
│   └── 0000-01-01-intro.md
├── script/                 # Development utility scripts
│   ├── setup              # Install dependencies
│   ├── server             # Run local dev server
│   ├── cibuild            # CI build with HTML validation
│   └── stage              # Staging deployment
├── _config.yml            # Jekyll configuration
├── Gemfile                # Ruby dependencies
├── index.html             # Presentation entry point
└── .editorconfig          # Code style configuration
```

## Key Commands

```bash
# Install dependencies
script/setup

# Run local development server
script/server
# Or directly: bundle exec jekyll serve

# Build and validate HTML (CI)
script/cibuild

# Install Ruby gems only
bundle install
```

## Development Workflow

1. **Adding Slides**: Create new Markdown files in `_posts/` with format `YYYY-MM-DD-title.md`
2. **Slide Front Matter**: Each slide file requires YAML front matter:
   ```yaml
   ---
   layout: slide
   title: Your Slide Title
   ---
   ```
3. **Local Preview**: Run `script/server` and open `http://localhost:4000`
4. **Build Output**: Generated site goes to `_site/` (gitignored)

## Code Style Conventions

From `.editorconfig`:
- **General files**: Tab indentation (4 spaces), LF line endings, UTF-8
- **JSON, JS, CSS, SCSS, YML, HTML**: Space indentation (2 spaces)
- **Markdown**: Space indentation (4 spaces), preserve trailing whitespace, ensure final newline

## Configuration Details

Key settings in `_config.yml`:
- **Markdown processor**: kramdown with rouge highlighter
- **Theme**: Solarized dark
- **Slide dimensions**: 1000x920px
- **Reveal.js features**: Progress bar, keyboard/touch navigation, history tracking
- **Slide numbering**: "c/t" format (current/total)

## Dependencies

**Ruby (Gemfile):**
- github-pages (>= 207) - GitHub Pages publishing
- html-proofer (>= 3.13.0) - HTML validation
- tzinfo-data - Timezone data

**Jekyll Plugins:**
- jemoji - Emoji support in Markdown

## Testing/Validation

- **HTML Validation**: html-proofer runs during CI build via `script/cibuild`
- **No unit testing framework** - validation is through HTML proofing only

## Important Notes for AI Assistants

1. **Slide File Naming**: Always use `YYYY-MM-DD-title.md` format in `_posts/`
2. **Layout System**: Use `slide` layout for individual slides, `presentation` for full decks
3. **Liquid Templates**: Jekyll uses Liquid syntax in `_includes/` and `_layouts/`
4. **No baseurl**: The `baseurl` in `_config.yml` is commented out for GitHub Pages compatibility
5. **reveal.js**: Presentation features are configured in `_config.yml` under reveal.js settings
6. **Build artifacts**: Never commit `_site/`, `.sass-cache/`, `.jekyll-metadata`, or `.bundle/`

## Git Workflow

- Feature branches for changes
- CI/CD via GitHub Pages and html-proofer validation
- Staging deployment available via `script/stage` (internal)

## License

MIT License (Copyright 2016 Thomas Friese)
