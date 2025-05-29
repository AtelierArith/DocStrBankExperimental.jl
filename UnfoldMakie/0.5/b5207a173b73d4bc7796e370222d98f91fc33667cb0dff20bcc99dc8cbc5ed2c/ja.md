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

トポプロットのシリーズをプロットします。この関数は、`data`の`:time`列に対して`combinefun = mean`を取ります。

  * `fig`    図オブジェクト。
  * `data::Union{<:Observable,<:AbstractMatrix}`   サイズ = (n*channel, n*topoplots)の行列。
  * `layout::Vector{Tuple{Int64, Int64}}`   各トポプロットの座標を持つタプルのベクター。
  * `topoplot_xlabels::Vector{String}`   各トポプロットのxlablesのベクター。
  * `topo_axis::NamedTuple = (;)`   ここでは、トポプロット軸の設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?Axis`と入力してください。   デフォルト: (aspect = 1, title = "", xgridvisible = false, xminorgridvisible = false, xminorticksvisible = false, xticksvisible = false, xticklabelsvisible = false, xlabelvisible = true, ygridvisible = false, yminorgridvisible = false, yminorticksvisible = false, yticksvisible = false, yticklabelsvisible = false, leftspinevisible = false, rightspinevisible = false, topspinevisible = false, bottomspinevisible = false, xpanlock = true, ypanlock = true, xzoomlock = true, yzoomlock = true, xrectzoom = false, yrectzoom = false)
  * `topo_attributes::NamedTuple = (;)`   ここでは、トポプロットの補間設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?Topoplot.topoplot`と入力してください。   デフォルト: interp_resolution = (128, 128), interpolation = CloughTocher()。
  * `positions::Vector{Point{2, Float32}}`   チャンネルの位置。すべてのユニークな電極のxおよびy位置のリスト。

**戻り値:** `Tuple{Figure, Vector{Any}}`。
