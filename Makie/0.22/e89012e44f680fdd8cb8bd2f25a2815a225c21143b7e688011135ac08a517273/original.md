```
density(values)
```

Plot a kernel density estimate of `values`.

## Plot type

The plot type alias for the `density` function is `Density`.

## Attributes

**`alpha`** =  `1.0`  — The alpha value of the colormap or color attribute. Multiple alphas like in plot(alpha=0.2, color=(:red, 0.5), will get multiplied.

**`bandwidth`** =  `automatic`  — Kernel density bandwidth, determined automatically if `automatic`.

**`boundary`** =  `automatic`  — Boundary of the density estimation, determined automatically if `automatic`.

**`color`** =  `@inherit patchcolor`  — Usually set to a single color, but can also be set to `:x` or `:y` to color with a gradient. If you use `:y` when `direction = :x` (or vice versa), note that only 2-element colormaps can work correctly.

**`colormap`** =  `@inherit colormap`  — *No docs available.*

**`colorrange`** =  `Makie.automatic`  — *No docs available.*

**`colorscale`** =  `identity`  — *No docs available.*

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`direction`** =  `:x`  — The dimension along which the `values` are distributed. Can be `:x` or `:y`.

**`inspectable`** =  `@inherit inspectable`  — *No docs available.*

**`linestyle`** =  `nothing`  — *No docs available.*

**`npoints`** =  `200`  — The resolution of the estimated curve along the dimension set in `direction`.

**`offset`** =  `0.0`  — Shift the density baseline, for layering multiple densities on top of each other.

**`strokearound`** =  `false`  — *No docs available.*

**`strokecolor`** =  `@inherit patchstrokecolor`  — *No docs available.*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *No docs available.*

**`weights`** =  `automatic`  — Assign a vector of statistical weights to `values`.
