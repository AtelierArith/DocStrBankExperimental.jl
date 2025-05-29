```
plot_channelimage!(f::Union{GridPosition, GridLayout, Figure}, data::Union{DataFrame,AbstractMatrix}, positions::Vector{Point{2,Float32}}, ch_names::Vector{String}; kwargs...)
plot_channelimage(data::Union{DataFrame, AbstractMatrix}, positions::Vector{Point{2,Float32}}, ch_names::Vector{String}; kwargs...)
```

チャネル画像をプロットする

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための `Figure`、`GridLayout`、または `GridPosition`。
  * `data::Union{DataFrame, AbstractMatrix}`   データを含む DataFrame または行列。   データは 1 行 - 1 チャンネルの形式である必要があります。
  * `positions::Vector{Point{2,Float32}}`   EEG レイアウト座標を持つベクトル。
  * `ch_names::Vector{String}`   チャンネル名を持つベクトル。
  * `times::Vector = range(-0.3, 1.2, length = size(data, 2))`   x 軸の時間範囲。
  * `sorting_variables::Vector = [:y, :x]`   y 軸上のチャンネルをソートする方法。   例えば、スカルプ上のチャンネル位置 (x, y) またはチャンネル名でソートできます。
  * `sorting_reverse::Vector = [:false, :false]`  ソート変数を逆にするべきかどうか？

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトが一致するまでサイクルされます。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "時間", ylabel = "チャンネル", yticklabelsize = 14) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/) を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) から任意のマッピングを使用してください* 

**visual =** (colormap = Makie.Reverse{String}("RdBu"),) - *[`Makie.heatmap`](https://docs.makie.org/stable/reference/plots/heatmap/) の `kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "電圧 [µV]") - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/) の `kwargs...` を使用してください* 

**戻り値:** チャネル画像を表示する `Figure`。
