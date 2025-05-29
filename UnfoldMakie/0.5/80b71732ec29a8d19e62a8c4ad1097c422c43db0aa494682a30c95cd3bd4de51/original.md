```
plot_designmatrix!(f::Union{GridPosition, GridLayout, Figure}, data::Unfold.DesignMatrix; kwargs...)
plot_designmatrix(data::Unfold.DesignMatrix; kwargs...)
```

Plot a designmatrix. 

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Unfold.DesignMatrix`
      Data for the plot visualization.

## Keyword arguments (kwargs)

  * `standardize_data::Bool = false`
      Indicates whether the data is standardized by pointwise division of the data with its sampled standard deviation.
  * `sort_data::Bool = false`
      Indicates whether the data is sorted. It uses `sortslices()` of Base Julia.
  * `xticks::Num = nothing`
      Specifies the number of labels displayed on the x-axis.

      * `xticks = 0`: No labels are displayed.
      * `xticks = 1`: Only the first label is displayed.
      * `xticks = 2`: The first and last labels are displayed.
      * `2 < xticks < number of labels`: The labels are evenly distributed across the axis.
      * `xticks ≥ number of labels`: All labels are displayed.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Conditions", ylabel = "Trials", xticklabelrotation = 0.39) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = :roma,) - *use `kwargs...` of [`Makie.heatmap`](https://docs.makie.org/stable/reference/plots/heatmap/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "") - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the Design matrix. 
