```
rainclouds!(ax, category_labels, data_array; plot_boxplots=true, plot_clouds=true, kwargs...)
```

Plot a violin (/histogram), boxplot and individual data points with appropriate spacing between each.

# Arguments

  * `ax`: Axis used to place all these plots onto.
  * `category_labels`: Typically `Vector{String}` with a label for each element in `data_array`
  * `data_array`: Typically `Vector{Float64}` used for to represent the datapoints to plot.

# Keywords

  * `gap=0.2`: Distance between elements of x-axis.
  * `side=:left`: Can take values of `:left`, `:right`, determines where the violin plot will be, relative to the scatter points
  * `dodge`: vector of `Integer`` (length of data) of grouping variable to create multiple side-by-side boxes at the same x position
  * `dodge_gap = 0.03`: spacing between dodged boxes
  * `n_dodge`: the number of categories to dodge (defaults to maximum(dodge))
  * `color`: a single color, or a vector of colors, one for each point

## Violin/Histogram Plot Specific Keywords

  * `clouds=violin`: [violin, hist, nothing] to show cloud plots either as violin or histogram plot, or no cloud plot.
  * `hist_bins=30`: if `clouds=hist`, this passes down the number of bins to the histogram call.
  * `cloud_width=1.0`: Determines size of violin plot. Corresponds to `width` keyword arg in

`violin`.

  * `orientation=:vertical` orientation of raindclouds (`:vertical` or `:horizontal`)
  * `violin_limits=(-Inf, Inf)`: specify values to trim the `violin`. Can be a `Tuple` or a `Function` (e.g. `datalimits=extrema`)

## Box Plot Specific Keywords

  * `plot_boxplots=true`: Boolean to show boxplots to summarize distribution of data.
  * `boxplot_width=0.1`: Width of the boxplot in category x-axis absolute terms.
  * `center_boxplot=true`: Determines whether or not to have the boxplot be centered in the category.
  * `whiskerwidth=0.5`: The width of the Q1, Q3 whisker in the boxplot. Value as a portion of the `boxplot_width`.
  * `strokewidth=1.0`: Determines the stroke width for the outline of the boxplot.
  * `show_median=true`: Determines whether or not to have a line should the median value in the boxplot.
  * `boxplot_nudge=0.075`: Determines the distance away the boxplot should be placed from the   center line when `center_boxplot` is `false`. This is the value used to recentering the   boxplot.
  * `show_boxplot_outliers`: show outliers in the boxplot as points (usually confusing when

paired with the scatter plot so the default is to not show them)

## Scatter Plot Specific Keywords

  * `side_nudge`: Default value is 0.02 if `plot_boxplots` is true, otherwise `0.075` default.
  * `jitter_width=0.05`: Determines the width of the scatter-plot bar in category x-axis absolute terms.
  * `markersize=2`: Size of marker used for the scatter plot.

## Axis General Keywords

  * `title`
  * `xlabel`
  * `ylabel`
