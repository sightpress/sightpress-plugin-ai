# SightPress AI

`sightpress/plugin-ai`: the official SightPress plugin for optional AI
assistance. Licensed GPL-2.0-or-later.

> **Status:** pre-M0.

AI is always optional: every workflow works fully with this plugin off, it
uses the tenant's **own** provider key (bring your own key), and every piece of
AI output is saved as `ai_draft` until a human reviews it — never published
automatically.

It adds:

- **BYOK AI provider connections**, configured install-wide.
- **Draft image descriptions** (alt text and long descriptions) and **SEO/AIO
  description drafts**, always shown for review before they count as
  `human`-reviewed.
- **Theme critique** for the theme generator, and **text-to-speech audio
  versions** of content.

Other plugins and core features that can be enhanced by AI show no control
until this plugin is enabled and connected; they never call an AI provider
directly, only through the `Ai` port this plugin fills.

## Development

```bash
composer install
vendor/bin/phpunit          # on PluginTestCase, enabled and disabled
vendor/bin/phpstan analyse
npx playwright test         # every manifest route, with axe-core
```

Fake providers and recorded responses only; CI never uses real keys or calls a
real AI provider. Check out `sightpress/core` as a sibling and require it with
`COMPOSER=composer.dev.json composer install` to run the test kernel. The full
plugin specification is in `plugins.md` §1.1.
