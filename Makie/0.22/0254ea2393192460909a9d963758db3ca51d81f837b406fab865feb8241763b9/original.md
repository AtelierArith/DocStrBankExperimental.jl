```
hexbin(xs, ys; kwargs...)
```

Plots a heatmap with hexagonal bins for the observations `xs` and `ys`.

## Plot type

The plot type alias for the `hexbin` function is `Hexbin`.

## Attributes

**`alpha`** =  `1.0`  — The alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.

**`bins`** =  `20`  — If an `Int`, sets the number of bins in x and y direction. If a `NTuple{2, Int}`, sets the number of bins for x and y separately.

**`cellsize`** =  `nothing`  — If a `Real`, makes equally-sided hexagons with width `cellsize`. If a `Tuple{Real, Real}` specifies hexagon width and height separately.

**`colormap`** =  `@inherit colormap :viridis`  — Sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.

**`colorrange`** =  `automatic`  — The values representing the start and end points of `colormap`.

**`colorscale`** =  `identity`  — The color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.

**`highclip`** =  `automatic`  — The color for any value above the colorrange.

**`lowclip`** =  `automatic`  — The color for any value below the colorrange.

**`nan_color`** =  `:transparent`  — The color for NaN values.

**`strokecolor`** =  `:black`  — *No docs available.*

**`strokewidth`** =  `0`  — *No docs available.*

**`threshold`** =  `1`  — The minimal number of observations in the bin to be shown. If 0, all zero-count hexagons fitting into the data limits will be shown.

**`weights`** =  `nothing`  — Weights for each observation.  Can be `nothing` (each observation carries weight 1) or any `AbstractVector{<: Real}` or `StatsBase.AbstractWeights`.
