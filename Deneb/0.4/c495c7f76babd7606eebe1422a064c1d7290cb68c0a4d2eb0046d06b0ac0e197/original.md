```
resolve(type; channels...)
resolve(type, channel, option)
```

Creates a `ResolveSpec`. The `type` indicates the resolution to be defined: `scale`, `axis`, or `legend`.

For scales, resolution can be specified for every channel. For axes, resolutions can be defined for positional channels (`x`, `y`, `xOffset`, `yOffset`). For legends, resolutions can be defined for non-positional channels (`color`, `opacity`, `shape`, and `size`).

There are two options to resolve a scale, axis, or legend: `shared` and `independent`. Independent scales imply independent axes and legends.

The defaults are documented in Vega-Lite's [documentation](https://vega.github.io/vega-lite/docs/resolve.html).

# Example

```
resolve(:scale, color=:independent)
```
