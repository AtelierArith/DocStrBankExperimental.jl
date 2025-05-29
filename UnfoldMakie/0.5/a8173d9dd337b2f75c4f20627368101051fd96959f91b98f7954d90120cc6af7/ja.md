```
plot_circular_topoplots!(f, data::DataFrame; kwargs...)
```

using ColorSchemes: topo using ColorSchemes: topo using ColorSchemes: topo     plot*circular*topoplots(data::DataFrame; kwargs...)

円形EEGトポプロットをプロットします。

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための`Figure`、`GridLayout`、または`GridPosition`。
  * `data::DataFrame`   データキー（列`:y, :yhat, :estimate`）と`:position`（列`:pos, :position, :positions`）を持つDataFrame。

## キーワード引数 (kwargs)

  * `predictor::Vector{Any} = :predictor`   円周上のトポプロットの位置を定義する円形予測子の値。`predictor_bounds`の周りにマッピングされます。
  * `predictor_bounds::Vector{Int64} = [0, 360]`   予測子の範囲。軸ラベルに関連します。
  * `positions::Vector{Point{2, Float32}} = nothing`   [`plot_topoplot`](@ref topo_vis)の位置。
  * `center_label::String = ""`   円の中心に表示されるテキスト。
  * `plot_radius::String = 0.8`   公式により計算された円形トポプロット系列プロットの半径：`radius = (minwidth * plot_radius) / 2`。
  * `labels::Vector{String} = nothing`   [`plot_topoplots`](@ref topo_vis)のラベル。
  * `topo_axis::NamedTuple = (;)`   トポプロット軸の設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで`?Axis`と入力してください。   デフォルト: (width = GridLayoutBase.Relative(0.2f0), height = GridLayoutBase.Relative(0.2f0), aspect = 1)
  * `topo_attributes::NamedTuple = (;)`   トポプロットの補間設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで`?Topoplot.topoplot`と入力してください。   デフォルト: interp_resolution = (128, 128), interpolation = CloughTocher()

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトがサイクルされて一致するまで続きます。

`;`を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)の`kwargs...`を使用してください* 

**axis =** (xlabel = "Time", aspect = 1) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)の`kwargs...`を使用してください* 

**layout =** (show*legend = false, use*colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *この[ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)を確認してください* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)の任意のマッピングを使用してください* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label*scatter = true, label*text = false, bounding*geometry = GeometryBasics.Circle) - *[`Topoplot.eeg*topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/)の`kwargs...`を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)の`kwargs...`を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "Voltage [µV]", colormap = Makie.Reverse{Symbol}(:RdBu)) - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)の`kwargs...`を使用してください* 

**戻り値:** 円形トポプロット系列を表示する`Figure`。
