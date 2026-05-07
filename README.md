# CodexMod

CodexMod is an experimental Scratch editor mod built from the Scratch editor monorepo. It keeps the familiar Scratch-style editor, then adds custom visual settings, extra block experiments, editor polish, and mod-specific branding.

Current version: **1.0**

This mod was made entirely by Codex using GPT-5.5.

## Status

CodexMod is a work-in-progress mod for local testing and experimentation. Some features are stable enough to use, while some experimental features are intentionally hidden or disabled until fixed.

Known disabled features:

- JavaScript extension: disabled because it is currently broken.
- BigInt extension: disabled because it is currently broken.

## Features

### Branding

- Top-left logo changed to `CodexMod`.
- Browser tab/title updated for the mod.
- Project title defaults to `CodexMod Project`.
- About button added to the top bar.
- About window shows the mod name, version, summary, and Codex/GPT-5.5 credit.

### Appearance

- Toggleable dark mode in settings.
- Dark block colors option in settings.
- Scratch 3.0 block colors.
- Scratch 2.0 block colors.
- Scratch 1.4 block colors.
- Multiple accent color options, including purple, blues, red, green, orange, cyan, and extra variants.
- Dark mode gradients removed for cleaner readability.
- Settings menu icons added for dark mode and block color modes.

### Editor Effects

- Particle effects when snapping blocks.
- UI tweaks across the editor for a more modded feel.
- Hidden disabled buttons where possible.
- Backpack support enabled where supported by the local editor.

### Blocks

- Delisted/obsolete blocks added back under obsolete subcategories.
- Obsolete blocks added across base categories.
- Debug category added at the bottom of base categories.
- Debug blocks use beige styling.
- Debug blocks include:
  - `log`
  - `warning`
  - `error`
  - `alert`
  - comment reporter/command style blocks
  - comment hat variation
  - comment C-block variation

### Logs

- Logs tab added next to the Sounds tab.
- Debug category blocks write to the logs tab.
- Log levels use different text colors.
- Alerts can open an alert window when supported by the browser runtime.

### Sprites And Assets

- Default sprite changed to Cat 2.
- Cat 1 removed from normal use.
- Other cat sprites/costumes hidden from the libraries.
- Library footer text explains removed assets were deleted for legal reasons.

### Sound Editor

Extra sound effects were added or exposed for testing:

- Echo
- Low pass
- High pass
- EQ
- Custom speed/pitch effect

### Paint Editor Experiments

Paint editor experiments were started, including:

- Outline pen idea
- Opacity slider idea
- Outline style idea
- Extra shape ideas

These may still need more polish depending on the current build state.

### Project Format

- Project saves were adjusted toward a `.cmp` CodexMod project file type.
- Compatibility with normal Scratch project flows may vary while this is experimental.

## Repository Layout

This repo is based on the Scratch editor monorepo layout.

```text
packages/
  scratch-gui/              React editor UI
  scratch-vm/               Scratch virtual machine and blocks runtime
  scratch-render/           WebGL renderer
  scratch-svg-renderer/     SVG processing
  task-herder/              async task scheduler package
  scratch-media-lib-scripts/ media library scripts
scripts/                    repo utility scripts
```

Most CodexMod editor UI changes live in `packages/scratch-gui`.
Most runtime/block behavior changes live in `packages/scratch-vm`.

## Requirements

- Node.js compatible with this repository.
- npm.
- A modern browser.

If dependencies are not installed yet, run:

```sh
npm ci
```

## Run Locally

From the repository root:

```sh
npm start
```

The editor is usually served by webpack dev server. If you need a specific port for local testing, run from `packages/scratch-gui`:

```sh
npx webpack serve --port 8601 --no-watch-options-stdin
```

Then open:

```text
http://localhost:8601/
```

If the browser shows stale UI, hard refresh with `Ctrl+F5`.

## Build

Build everything from the repository root:

```sh
npm run build
```

Build only the GUI package:

```sh
npm run build --workspace=packages/scratch-gui
```

## Tests

Run all workspace tests:

```sh
npm test
```

Run GUI tests:

```sh
npm test --workspace=packages/scratch-gui
```

Run VM tests:

```sh
npm test --workspace=packages/scratch-vm
```

Some Scratch test suites are large and may need browser or integration-test setup.

## Development Notes

- Keep Scratch GUI changes in `packages/scratch-gui`.
- Keep VM extension/block runtime changes in `packages/scratch-vm`.
- Run i18n extraction after changing user-visible React strings:

```sh
npm run i18n:src --workspace=packages/scratch-gui
```

- Run i18n extraction after changing VM extension strings:

```sh
npm run i18n:src --workspace=packages/scratch-vm
```

## Experimental Extension Status

The JavaScript and BigInt extensions exist in the source tree, but they are disabled for now because they are broken. They should not appear in the extension library and should not be registered by the VM until fixed.

When re-enabling them later, check both:

- `packages/scratch-gui/src/lib/libraries/extensions/index.jsx`
- `packages/scratch-vm/src/extension-support/extension-manager.js`

## Legal And Credits

CodexMod is an unofficial experimental mod. It is not affiliated with, endorsed by, or maintained by the Scratch Foundation.

Scratch is developed by the Scratch Foundation. Scratch names, assets, and trademarks belong to their respective owners. Some cat assets are hidden or removed in this mod for legal reasons.

CodexMod modifications were made by Codex using GPT-5.5.

## License

This repository includes upstream Scratch editor code and keeps the existing repository license files. See `LICENSE` and `TRADEMARK` for the current legal terms included with this repo.
