```
plot_erpgrid(data::Union{Matrix{<:Real}, DataFrame}, positions::Vector; kwargs...)
plot_erpgrid!(f::Union{GridPosition, GridLayout, Figure}, data::Union{Matrix{<:Real}, DataFrame}, positions::Vector, ch_names::Vector{String}; kwargs...)
```

ERP画像をプロットします。

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための`Figure`、`GridLayout`、または`GridPosition`。
  * `data::Union{Matrix{<:Real}, DataFrame}`   プロットの視覚化のためのデータ。   データは1行 - 1チャネルの形式である必要があります。
  * `positions::Vector{Point{2,Float}}`    電極の位置。
  * `ch_names::Vector{String}`   チャネル名のベクター。
  * `hlines_grid_axis::NamedTuple = (;)`   ここでは、すべてのサブ軸のhlinesの設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?hlines`と入力してください。   デフォルト: (color = :gray, linewidth = 0.5)
  * `vlines_grid_axis::NamedTuple = (;)`   ここでは、すべてのサブ軸のvlinesの設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?vlines`と入力してください。   デフォルト: (color = :gray, linewidth = 0.5, ymin = 0.2, ymax = 0.8)
  * `lines_grid_axis::NamedTuple = (;)`   ここでは、すべてのサブ軸の線の設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?lines`と入力してください。   デフォルト: (color = :deepskyblue3,)
  * `labels_grid_axis::NamedTuple = (;)`   ここでは、すべてのサブ軸のラベルの設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで`?text`と入力してください。   デフォルト: (color = :gray, fontsize = 12, align = (:left, :top), space = :relative)
  * `indicator_grid_axis::NamedTuple = (;)`   ここでは、インジケーター軸の設定を変更できます。   デフォルト: (fontsize = 12, xlim = [-0.04, 1.0], ylim = [-0.04, 1.0], arrows*start = GeometryBasics.Point{2, Float32}[[0.0, 0.0], [0.0, 0.0]], arrows*dir = GeometryBasics.Vec{2, Float32}[[0.0, 0.1], [0.1, 0.0]], arrows*kwargs = (arrowsize = 10,), text*x*coords = (0.02, 0), text*x*kwargs = (text = "Time [s]", align = (:left, :top), fontsize = 12), text*y*coords = (-0.008, 0.01), text*y_kwargs = (text = "Voltage [µV]", align = (:left, :baseline), fontsize = 12, rotation = 1.5707963267948966))
  * `subaxes::NamedTuple = (;)`   ここでは、すべてのサブ軸の設定を柔軟に変更できます。例えば、幅を広くしたり短くしたりできます。   すべてのオプションを見るには、REPLで`?Axis`と入力してください。   デフォルト: (width = GridLayoutBase.Relative(0.1f0), height = GridLayoutBase.Relative(0.1f0))

## キーワード引数 (kwargs)

  * `drawlabels::Bool = false`   各波形の上にチャネルラベルを描画します。
  * `times::Vector = 1:size(data, 2)`   `size()`のベクター。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトが循環して一致するまで続きます。

`;`を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)の`kwargs...`を使用してください* 

**axis =** (width = GridLayoutBase.Relative(1.05f0), height = GridLayoutBase.Relative(1.05f0)) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)の`kwargs...`を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この[ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)から任意のマッピングを使用してください* 

**visual =** (colormap = :roma,) - *[`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)の`kwargs...`を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)の`kwargs...`を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)の`kwargs...`を使用してください* 

**戻り値:** ERPグリッドを表示する`Figure`。
