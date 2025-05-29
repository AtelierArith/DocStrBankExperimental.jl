```
plot_erpgrid(data::Union{Matrix{<:Real}, DataFrame}, positions::Vector; kwargs...)
plot_erpgrid!(f::Union{GridPosition, GridLayout, Figure}, data::Union{Matrix{<:Real}, DataFrame}, positions::Vector, ch_names::Vector{String}; kwargs...)
```

Plot an ERP image.

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{Matrix{<:Real}, DataFrame}`
      Data for the plot visualization.
      Data should has a format of 1 row - 1 channel.
  * `positions::Vector{Point{2,Float}}` 
      Electrode positions.
  * `ch_names::Vector{String}`
      Vector with channel names.
  * `hlines_grid_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the hlines on all subaxes.
      To see all options just type `?hlines` in REPL.
      Defaults: (color = :gray, linewidth = 0.5)
  * `vlines_grid_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the vlines on all subaxes.
      To see all options just type `?vlines` in REPL.
      Defaults: (color = :gray, linewidth = 0.5, ymin = 0.2, ymax = 0.8)
  * `lines_grid_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the lines on all subaxes.
      To see all options just type `?lines` in REPL.
      Defaults: (color = :deepskyblue3,)
  * `labels_grid_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the labels on all subaxes.
      To see all options just type `?text` in REPL.
      Defaults: (color = :gray, fontsize = 12, align = (:left, :top), space = :relative)
  * `indicator_grid_axis::NamedTuple = (;)`
      Here you can change configurations of inidcator axis.
      Defaults: (fontsize = 12, xlim = [-0.04, 1.0], ylim = [-0.04, 1.0], arrows*start = GeometryBasics.Point{2, Float32}[[0.0, 0.0], [0.0, 0.0]], arrows*dir = GeometryBasics.Vec{2, Float32}[[0.0, 0.1], [0.1, 0.0]], arrows*kwargs = (arrowsize = 10,), text*x*coords = (0.02, 0), text*x*kwargs = (text = "Time [s]", align = (:left, :top), fontsize = 12), text*y*coords = (-0.008, 0.01), text*y_kwargs = (text = "Voltage [µV]", align = (:left, :baseline), fontsize = 12, rotation = 1.5707963267948966))
  * `subaxes::NamedTuple = (;)`
      Here you can flexibly change configurations of all subaxes. F.e. make them wider or shorter
      To see all options just type `?Axis` in REPL.
      Defaults: (width = GridLayoutBase.Relative(0.1f0), height = GridLayoutBase.Relative(0.1f0))

## Keyword arguments (kwargs)

  * `drawlabels::Bool = false`
      Draw channels labels over each waveform.
  * `times::Vector = 1:size(data, 2)`
      Vector of `size()`.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (width = GridLayoutBase.Relative(1.05f0), height = GridLayoutBase.Relative(1.05f0)) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = :roma,) - *use `kwargs...` of [`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying ERP grid.
