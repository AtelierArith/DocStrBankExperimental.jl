```
rainclouds!(ax, category_labels, data_array; plot_boxplots=true, plot_clouds=true, kwargs...)
```

Plot a violin (/histogram), boxplot and individual data points with appropriate spacing between each.

# Arguments

  * `ax`: Axis used to place all these plots onto.
  * `category_labels`: Typically `Vector{String}` with a label for each element in `data_array`
  * `data_array`: Typically `Vector{Float64}` used for to represent the datapoints to plot.

# Keywords

## Plot type

The plot type alias for the `rainclouds` function is `RainClouds`.

## Attributes

**`boxplot_nudge`** =  `0.075`  — Determines the distance away the boxplot should be placed from the center line when `center_boxplot` is `false`. This is the value used to recentering the boxplot.

**`boxplot_width`** =  `0.1`  — Width of the boxplot on the category axis.

**`center_boxplot`** =  `true`  — Whether or not to center the boxplot on the category.

**`cloud_width`** =  `0.75`  — Determines size of violin plot. Corresponds to `width` keyword arg in `violin`.

**`clouds`** =  `violin`  — [`violin`, `hist`, `nothing`] how to show cloud plots, either as violin or histogram plots, or not at all.

**`color`** =  `@inherit patchcolor`  — A single color, or a vector of colors, one for each point.

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`dodge`** =  `automatic`  — Vector of `Integer` (length of data) of grouping variable to create multiple side-by-side boxes at the same x position

**`dodge_gap`** =  `0.01`  — Spacing between dodged boxes.

**`gap`** =  `0.2`  — Distance between elements on the main axis (depending on `orientation`).

**`hist_bins`** =  `30`  — If `clouds=hist`, this passes down the number of bins to the histogram call.

**`jitter_width`** =  `0.05`  —  Determines the width of the scatter-plot bar in category x-axis absolute terms.

**`markersize`** =  `2.0`  — Size of marker used for the scatter plot.

**`n_dodge`** =  `automatic`  — The number of categories to dodge (defaults to `maximum(dodge)`)

**`orientation`** =  `:vertical`  — Orientation of rainclouds (`:vertical` or `:horizontal`)

**`plot_boxplots`** =  `true`  — Whether to show boxplots to summarize distribution of data.

**`show_boxplot_outliers`** =  `false`  — Show outliers in the boxplot as points (usually confusing when paired with the scatter plot so the default is to not show them)

**`show_median`** =  `true`  — Determines whether or not to have a line for the median value in the boxplot.

**`side`** =  `:left`  — Can take values of `:left`, `:right`, determines where the violin plot will be, relative to the scatter points

**`side_nudge`** =  `automatic`  — Scatter plot specific.  Default value is 0.02 if `plot_boxplots` is true, otherwise `0.075` default.

**`strokewidth`** =  `1.0`  — Determines the stroke width for the outline of the boxplot.

**`violin_limits`** =  `(-Inf, Inf)`  — Specify values to trim the `violin`. Can be a `Tuple` or a `Function` (e.g. `datalimits=extrema`)

**`whiskerwidth`** =  `0.5`  — The width of the Q1, Q3 whisker in the boxplot. Value as a portion of the `boxplot_width`.
