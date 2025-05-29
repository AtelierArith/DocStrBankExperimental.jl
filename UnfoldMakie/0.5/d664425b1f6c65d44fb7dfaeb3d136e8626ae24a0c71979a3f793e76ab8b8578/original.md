```
plot_parallelcoordinates(data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_parallelcoordinates!(f::Union{GridPosition, GridLayout, Figure}, data::Union{DataFrame, AbstractMatrix}; kwargs)
```

Plot a PCP (parallel coordinates plot).
Dimensions: conditions, channels, time, trials. 

## Arguments:

  * `f::Union{GridPosition, GridLayout, Figure}`   `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{DataFrame, AbstractMatrix}`
      Data for the plot visualization.

## Keyword arguments (kwargs)

  * `normalize::Symbol = nothing`
      If `:minmax`, normalize each axis to their respective min-max range.
  * `ax_labels::Vector{String} = nothing`
      Specify axis labels. 
      Should be a vector of labels with length equal to the number of unique `mapping.x` values.
      Example: `ax_labels = ["Fz", "Cz", "O1", "O2"]`.
  * `ax_ticklabels::Symbol = :outmost`
      Specify tick labels on axis.

      * `:all` - show all labels on all axes.
      * `:left` - show all labels on the left axis, but only min and max on others.
      * `:outmost` - show labels on min and max of all other axes.
      * `:none` - remove all labels.
  * `bend::Bool = false`
      Change straight lines between the axes to curved ("bent") lines using spline interpolation.
      Note: While this makes the plot look cool, it is not generally recommended to bent the lines, as interpretation   suffers, and the resulting visualizations can be potentially missleading.
  * `visual.alpha::Number = 0.5`
      Change of line transparency.

## Defining the axes

  * `mapping.x = :channel, mapping.y = :estimate`.
      Overwrite what should be on the x and the y axes.
  * `mapping.color = :colorcolumn` 
      Split conditions by color. The default color is `:black`.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Channels", ylabel = "Time", title = "", xlabelpadding = 14, ylabelpadding = 26) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = :channel, y = (:estimate, :yhat, :y)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = ColorTypes.RGBA{Float32}[RGBA(0.0, 0.44705883, 0.69803923, 1.0), RGBA(0.9019608, 0.62352943, 0.0, 1.0), RGBA(0.0, 0.61960787, 0.4509804, 1.0), RGBA(0.8, 0.4745098, 0.654902, 1.0), RGBA(0.3372549, 0.7058824, 0.9137255, 1.0), RGBA(0.8352941, 0.36862746, 0.0, 1.0), RGBA(0.9411765, 0.89411765, 0.25882354, 1.0)], color = :black, alpha = 0.3) - *use `kwargs...` of [`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, title = "Conditions", merge = true, framevisible = false) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the Parallel coordinates plot.
