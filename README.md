# pj-rust-lib

`kata` template layer for Rust **library** crates under
yukimemi/*. Sits ABOVE [`yukimemi/pj-rust`](https://github.com/yukimemi/pj-rust)
under [`yukimemi/pj-base`](https://github.com/yukimemi/pj-base) in
the compose order; `pj-rust`'s CI matrix and tooling are the
baseline, this layer adds:

- A tag-driven `release.yml` that **publishes to crates.io and
  stamps the GitHub release page with auto-generated notes** —
  no cross-compile, no binary attach (libraries' canonical
  artifact is the crates.io tarball).
- A `kata:agents:rust-lib:*` marker block in `AGENTS.md` covering
  the lib release flow, MSRV / SemVer caveats, and the
  `cargo publish --dry-run` pre-flight.
- A baseline `.editorconfig`.

The companion preset is
[`yukimemi/pj-presets:rust-lib`](https://github.com/yukimemi/pj-presets)
(composes pj-base + pj-rust + pj-rust-lib).

## Apply

```sh
kata init github.com/yukimemi/pj-presets:rust-lib
```

Or from a kata-managed PJ that's already on the cli preset and
should be migrated to lib:

```sh
kata remove github.com/yukimemi/pj-rust-cli
kata add github.com/yukimemi/pj-rust-lib
kata apply
```

## Sibling layers

- [`pj-base`](https://github.com/yukimemi/pj-base) — language-agnostic
- [`pj-rust`](https://github.com/yukimemi/pj-rust) — Rust language
- [`pj-rust-cli`](https://github.com/yukimemi/pj-rust-cli) — sibling for binary crates
