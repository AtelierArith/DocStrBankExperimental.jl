```
plot_topoplotseries(f::Union{GridPosition, GridLayout, Figure}, data::Union{<:Observable{<:DataFrame},DataFrame}; kwargs...)
plot_topoplotseries!(data::Union{<:Observable{<:DataFrame},DataFrame}; kwargs...)
```

Multiple miniature topoplots in regular distances. 

## Arguments

  * `f::Union{GridPosition, GridLayout, GridLayoutBase.GridSubposition, Figure}`
      `Figure`, `GridLayout`, `GridPosition`, or `GridLayoutBase.GridSubposition` to draw the plot.
  * `data::Union{<:Observable{<:DataFrame},DataFrame}`
      DataFrame with data or Observable DataFrame.
      Requires a `time` column by default, but can be overridden by specifying `mapping=(; x=:my_column)` with any continuous or categorical column.

## Keyword arguments (kwargs)

  * `bin_width::Real = nothing`
      Number specifing the width of bin of continuous x-value in its units.
  * `bin_num::Real = nothing`
      Number of topoplots.
      Either `bin_width`, or `bin_num` should be specified. Error if they are both specified
      If `mapping.col` or `mapping.row` are categorical `bin_width` and `bin_num` stay as `nothing`.
  * `combinefun::Function = mean`
      Specify how the samples within `bin_width` are summarised.
      Example functions: `mean`, `median`, `std`.
  * `rasterize_heatmaps::Bool = true`
      Force rasterization of the plot heatmap when saving in `svg` format.
      Except for the interpolated heatmap, all lines/points are vectors.
      This is typically what you want, otherwise you get ~128x128 vectors per topoplot, which makes everything very slow.
  * `col_labels::Bool`, `row_labels::Bool = true`
      Shows column and row labels in faceting mode. (not implemented)
  * `positions::Vector{Point{2, Float32}} = nothing`
      Specify channel positions. Requires the list of x and y positions for all unique electrodes.
  * `labels::Vector{String} = nothing`
      Show labels for each electrode.
  * `interactive_scatter = nothing`
      Enable interactive mode.
      If you create `obs_tuple = Observable((0, 0, 0))` and pass it into `interactive_scatter` you can update the observable tuple with the indices of the clicked topoplot markers.
      `(0, 0, 0)` corresponds to the (row of topoplot layout, column of topoplot layout, electrode).
  * `topo_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of topoplots.
      To see all options just type `?Axis` in REPL.
  * `mapping = (; col = :time`, row = nothing, layout = nothing)
      `mapping.col` - specify x-value, can be any continuous or categorical variable.
      `mapping.row` - specify y-value, can be any continuous or categorical variable (not implemented yet).
      `mapping.layout` - arranges topoplots by rows when equals `:time`.
  * `topo_attributes::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot interoplation.
      To see all options just type `?Topoplot.topoplot` in REPL.
      Defaults: interp_resolution = (128, 128), interpolation = CloughTocher()
  * `topolabels_rounding = (; sigdigits = 3)`
      Rounding of the topo_axis labels.
      `sigdigits` - number of significant digits.
      `digits` - number of digits after the decimal point.
      Only one of `sigdigits` or `digits` should be provided.

## Shared plot configuration options

The shared plot options can be used as follows: `type = (; key = value, ...))`.
For example, `plot_x(...; colorbar = (; vertical = true, label = "Test"))`.
Multiple defaults will be cycled until match.

Placing `;` is important!

**figure =** NamedTuple() - *use `kwargs...` of [`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)* 

**axis =** (xlabel = "Time windows", aspect = Makie.DataAspect(), title = "", titlesize = 16, titlefont = :bold, ylabel = "", ylabelpadding = 25, xlabelpadding = 25, xpanlock = true, ypanlock = true, xzoomlock = true, yzoomlock = true, xrectzoom = false, yrectzoom = false) - *use `kwargs...` of  [`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)* 

**layout =** (show_legend = true, use_colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *check this [page](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing), col = (:time,), row = (nothing,)) - *use any mapping from [`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label_scatter = false, label_text = false, bounding_geometry = GeometryBasics.Circle, levels = nothing) - *use `kwargs...` of [`Topoplot.eeg_topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/)* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *use `kwargs...` of  [`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "Voltage [µV]") - *use `kwargs...` of  [`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)* 

**Return Value:** `Figure` displaying the Topoplot series.
