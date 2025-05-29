```
plot_butterfly(plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_butterfly(times::Vector, plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_butterfly!(f::Union{GridPosition, GridLayout, Figure}, plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
```

Plot a Butterfly plot.

## Arguments

  * `f::Union{GridPosition, GridLayout, Figure}`
      `Figure`, `GridLayout`, or `GridPosition` to draw the plot.
  * `data::Union{DataFrame, AbstractMatrix}`
      Data for the ERP plot visualization.
  * `kwargs...`
      Additional styling behavior. 
      Often used as: `plot_butterfly(df; visual = (; colormap = :romaO))`.

## Keyword arguments (kwargs)

  * `positions::Array = []` 
      Adds a topoplot as an inset legend to the provided channel positions. Must be the same length as `plot_data`.     To change the colors of the channel lines use the `topoposition_to_color` function.
  * `topolegend::Bool = true`
      Show an inlay topoplot with corresponding electrodes. Requires `positions`.
  * `topopositions_to_color::x -> pos_to_color_RomaO(x)`
      Change the line colors.
  * `topo_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot axis.
      To see all options just type `?Axis` in REPL.
      Defaults: (width = GridLayoutBase.Relative(0.35f0), height = GridLayoutBase.Relative(0.35f0), halign = 0.05, valign = 0.95, aspect = 1)
  * `topo_attributes::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot interoplation.
      To see all options just type `?Topoplot.topoplot` in REPL.
      Defaults: (head = (color = :black, linewidth = 1), label_scatter = (markersize = 10, strokewidth = 0.5), interpolation = TopoPlots.NullInterpolator())
  * `mapping = (;)`
      For highlighting specific channels.
      Example: `mapping = (; color = :highlight))`, where `:highlight` is variable with appopriate mapping.

**Return Value:** `Figure` displaying Butterfly plot.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Time", ylabel = "Voltage [µV]", yticklabelsize = 14, xtickformat = "{:.1f}") - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = false, use_colorbar = true, use_legend = true, hidespines = (:r, :t), hidedecorations = Dict{Symbol, Bool}(:label => 0, :ticks => 0, :ticklabels => 0)) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y), color = (:channel, :channels, :trial, :trials), positions = (:pos, :positions, :position, :topo_positions, :x, nothing), labels = (:labels, :label, :topoLabels, :sensor, nothing), group = (:channel,)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = nothing, color = nothing) - *use `kwargs...` of [`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, framevisible = false) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "", flipaxis = true) - *use `kwargs...` of  [`AlgebraOfGraphics.colorbar!`](@ref)* 

see also [`plot_erp`](@ref erp_vis)
