```
plot_circular_topoplots!(f, data::DataFrame; kwargs...)
```

using ColorSchemes: topo using ColorSchemes: topo using ColorSchemes: topo     plot*circular*topoplots(data::DataFrame; kwargs...)

Plot a circular EEG topoplot.

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::DataFrame`
      DataFrame with data keys (columns `:y, :yhat, :estimate`), and :position (columns `:pos, :position, :positions`).

## Keyword arguments (kwargs)

  * `predictor::Vector{Any} = :predictor`
      The circular predictor value, defines position of topoplot across the circle.   Mapped around `predictor_bounds`.
  * `predictor_bounds::Vector{Int64} = [0, 360]`
      The bounds of the predictor. Relevant for the axis labels.
  * `positions::Vector{Point{2, Float32}} = nothing`
      Positions of the [`plot_topoplot`](@ref topo_vis).
  * `center_label::String = ""`
      The text in the center of the cricle.
  * `plot_radius::String = 0.8`
      The radius of the circular topoplot series plot calucalted by formula: `radius = (minwidth * plot_radius) / 2`.
  * `labels::Vector{String} = nothing`
      Labels for the [`plot_topoplots`](@ref topo_vis).
  * `topo_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot axis.
      To see all options just type `?Axis` in REPL.
      Defaults: (width = GridLayoutBase.Relative(0.2f0), height = GridLayoutBase.Relative(0.2f0), aspect = 1)
  * `topo_attributes::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot interoplation.
      To see all options just type `?Topoplot.topoplot` in REPL.
      Defaults: interp_resolution = (128, 128), interpolation = CloughTocher()

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Time", aspect = 1) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = false, use_colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label_scatter = true, label_text = false, bounding_geometry = GeometryBasics.Circle) - *use `kwargs...` of [`Topoplot.eeg_topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "Voltage [µV]", colormap = Makie.Reverse{Symbol}(:RdBu)) - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the Circular topoplot series.
