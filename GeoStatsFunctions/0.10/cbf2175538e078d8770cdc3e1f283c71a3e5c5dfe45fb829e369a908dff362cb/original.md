```
funplot(f; [options])
```

Plot the geostatistical function `f` with given `options`.

## Common options:

  * `color`  - color
  * `size`   - size (line width)
  * `maxlag` - maximum lag
  * `labels` - variable names

## Empirical function options:

  * `style`       - style (line style)
  * `pointsize`   - size of points
  * `showtext`    - show text counts
  * `textsize`    - size of text counts
  * `showhist`    - show histogram
  * `histcolor`   - color of histogram

### Notes

This function will only work in the presence of a Makie.jl backend via package extensions in Julia v1.9 or later versions of the language.
