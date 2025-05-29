```
plot_basins_curves(fractions_cont [, prange]; kw...)
```

Plot the fractions of basins of attraction versus a parameter range/curve, i.e., visualize the output of [`global_continuation`](@ref). See also [`plot_basins_attractors_curves`](@ref) and [`plot_continuation_curves`](@ref).

## Keyword arguments

  * `style = :band`: how to visualize the basin fractions. Choices are `:band` for a band plot with cumulative sum = 1 or `:lines` for a lines plot of each basin fraction
  * `separatorwidth = 1, separatorcolor = "white"`: adds a line separating the fractions if the style is `:band`
  * `filler = NaN`: filler value to use for basin fractions for attractor IDs that do not exist at a continuation step when the style is `:lines` (filler is always `0` for `:band` style).
  * `axislegend_kwargs = (position = :lt,)`: propagated to `axislegend` if a legend is added
  * `series_kwargs = NamedTuple()`: propagated to the band or scatterline plot
  * Also all [common plotting keywords](@ref common_plot_kwargs).
