```
boxplot(x, y; kwargs...)
```

Draw a Tukey style boxplot. The boxplot has 3 components:

  * a `crossbar` spanning the interquartile (IQR) range with a midline marking the   median
  * an `errorbar` whose whiskers span `range * iqr`
  * points marking outliers, that is, data outside the whiskers

## Arguments

  * `x`: positions of the categories
  * `y`: variables within the boxes

## Plot type

The plot type alias for the `boxplot` function is `BoxPlot`.

## Attributes

**`color`** =  `@inherit patchcolor`  — *No docs available.*

**`colormap`** =  `@inherit colormap`  — *No docs available.*

**`colorrange`** =  `automatic`  — *No docs available.*

**`colorscale`** =  `identity`  — *No docs available.*

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`dodge`** =  `automatic`  — Vector of `Integer` (length of data) of grouping variable to create multiple side-by-side boxes at the same `x` position.

**`dodge_gap`** =  `0.03`  — Spacing between dodged boxes.

**`gap`** =  `0.2`  — Shrinking factor, `width -> width * (1 - gap)`.

**`inspectable`** =  `@inherit inspectable`  — *No docs available.*

**`marker`** =  `@inherit marker`  — *No docs available.*

**`markersize`** =  `@inherit markersize`  — *No docs available.*

**`mediancolor`** =  `@inherit linecolor`  — *No docs available.*

**`medianlinewidth`** =  `@inherit linewidth`  — *No docs available.*

**`n_dodge`** =  `automatic`  — *No docs available.*

**`notchwidth`** =  `0.5`  — Multiplier of `width` for narrowest width of notch.

**`orientation`** =  `:vertical`  — Orientation of box (`:vertical` or `:horizontal`).

**`outliercolor`** =  `automatic`  — *No docs available.*

**`outlierstrokecolor`** =  `@inherit markerstrokecolor`  — *No docs available.*

**`outlierstrokewidth`** =  `@inherit markerstrokewidth`  — *No docs available.*

**`range`** =  `1.5`  — Multiple of IQR controlling whisker length.

**`show_median`** =  `true`  — Show median as midline.

**`show_notch`** =  `false`  — Draw the notch.

**`show_outliers`** =  `true`  — Show outliers as points.

**`strokecolor`** =  `@inherit patchstrokecolor`  — *No docs available.*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *No docs available.*

**`weights`** =  `automatic`  — Vector of statistical weights (length of data). By default, each observation has weight `1`.

**`whiskercolor`** =  `@inherit linecolor`  — *No docs available.*

**`whiskerlinewidth`** =  `@inherit linewidth`  — *No docs available.*

**`whiskerwidth`** =  `0.0`  — Multiplier of `width` for width of T's on whiskers, or `:match` to match `width`.

**`width`** =  `automatic`  — Width of the box before shrinking.
