```
 eeg_topoplot_series(data::DataFrame,
    fig,
    data_inp::Union{<:Observable,<:AbstractMatrix};
    layout = nothing,
    topoplot_xlabels = nothing,
    labels = nothing,
    rasterize_heatmaps = true,
    interactive_scatter = nothing,
    highlight_scatter = false,
    topo_axis = (;),
    topo_attributes = (;),
    positions,
)
eeg_topoplot_series!(fig, data::DataFrame; kwargs..)
```

Plot a series of topoplots.  The function takes the `combinefun = mean` over the `:time` column of `data`.

  * `fig` 
      Figure object.
  * `data::Union{<:Observable,<:AbstractMatrix}`
      Matrix with size = (n*channel, n*topoplots).
  * `layout::Vector{Tuple{Int64, Int64}}`
      Vector of tuples with coordinates for each topoplot.
  * `topoplot_xlabels::Vector{String}`
      Vector of xlables for each topoplot.
  * `topo_axis::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot axis.
      To see all options just type `?Axis` in REPL.
      Defaults: (aspect = 1, title = "", xgridvisible = false, xminorgridvisible = false, xminorticksvisible = false, xticksvisible = false, xticklabelsvisible = false, xlabelvisible = true, ygridvisible = false, yminorgridvisible = false, yminorticksvisible = false, yticksvisible = false, yticklabelsvisible = false, leftspinevisible = false, rightspinevisible = false, topspinevisible = false, bottomspinevisible = false, xpanlock = true, ypanlock = true, xzoomlock = true, yzoomlock = true, xrectzoom = false, yrectzoom = false)
  * `topo_attributes::NamedTuple = (;)`
      Here you can flexibly change configurations of the topoplot interoplation.
      To see all options just type `?Topoplot.topoplot` in REPL.
      Defaults: interp_resolution = (128, 128), interpolation = CloughTocher().
  * `positions::Vector{Point{2, Float32}}`
      Channel positions. The list of x and y positions for all unique electrodes.

**Return Value:** `Tuple{Figure, Vector{Any}}`.
