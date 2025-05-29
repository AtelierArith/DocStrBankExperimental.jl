```
plot_topoplot!(f::Union{GridPosition, GridLayout, Figure}, data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}; positions::Vector, labels = nothing, kwargs...)
plot_topoplot(data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}; position::Vector, labels = nothing, kwargs...)
```

Plot a topoplot.

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}` 
      Data for the plot visualization.
  * `positions::Vector{Point{2, Float32}}`
      Positions used if `data` is not a `DataFrame`. Positions are generated from `labels` if `positions = nothing`.
  * `labels::Vector{String} = nothing`
      Labels used if `data` is not a DataFrame.
  * `high_chan = nothing` - channnel(s) to highlight by color.
  * `high_color = :darkgreen` - color for highlighting.
  * `topo_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot axis.
      To see all options just type `?Axis` in REPL.
      Defaults: (width = GridLayoutBase.Relative(1.0f0), height = GridLayoutBase.Relative(1.0f0), halign = 0.05, valign = 0.95, aspect = Makie.DataAspect())
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

**axis =** (xlabel = "Time", aspect = Makie.DataAspect()) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label_scatter = true, label_text = false, bounding_geometry = GeometryBasics.Circle) - *use `kwargs...` of [`Topoplot.eeg_topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "Voltage [µV]") - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the Topoplot.
