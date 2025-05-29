```
plot_splines(m::UnfoldModel; kwargs...)
plot_splines!(f::Union{GridPosition, GridLayout, Figure}, m::UnfoldModel; kwargs...)
```

Visualization of spline terms in an UnfoldModel. Two subplots are generated for each spline term:
1) the basis function of the spline; 2) the density of the underlying covariate.
Multiple spline terms are arranged across columns.
Dashed lines indicate spline knots.

## Arguments:

  * `f::Union{GridPosition, GridLayout, Figure}`   `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `m::UnfoldModel`
      UnfoldModel with splines.
  * `spline_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of spline subplots.
      To see all options just type `?Axis` in REPL.
      Defaults: (ylabel = "Spline value", xlabelvisible = false, xticklabelsvisible = false, ylabelvisible = true)
  * `density_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of density subplots.
      To see all options just type `?Axis` in REPL.
      Defaults: (xautolimitmargin = (0, 0), ylabel = "Density value")
  * `superlabel_config::NamedTuple = (;)`
      Here you can flexibly change configurations of the Label on the top of the plot.
      To see all options just type `?Label` in REPL.
      Defaults: (fontsize = 20, padding = (0, 0, 40, 0))

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** NamedTuple() - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = :viridis,) - *use `kwargs...` of [`Makie.series`](https://docs.makie.org/stable/reference/plots/series)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, title = "Splines", framevisible = false) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` with splines and their density for basis functions.
