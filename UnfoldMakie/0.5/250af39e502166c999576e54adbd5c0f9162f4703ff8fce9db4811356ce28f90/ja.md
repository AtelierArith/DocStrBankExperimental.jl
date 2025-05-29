```
plot_butterfly(plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_butterfly(times::Vector, plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_butterfly!(f::Union{GridPosition, GridLayout, Figure}, plot_data::Union{DataFrame, AbstractMatrix}; kwargs...)
```

バタフライプロットを描画します。

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための `Figure`、`GridLayout`、または `GridPosition`。
  * `data::Union{DataFrame, AbstractMatrix}`   ERPプロットの視覚化のためのデータ。
  * `kwargs...`   追加のスタイリング動作。    よく使われる例: `plot_butterfly(df; visual = (; colormap = :romaO))`。

## キーワード引数 (kwargs)

  * `positions::Array = []`    提供されたチャネル位置にインセットレジェンドとしてトポプロットを追加します。 `plot_data` と同じ長さである必要があります。 チャネルラインの色を変更するには、`topoposition_to_color` 関数を使用します。
  * `topolegend::Bool = true`   対応する電極を持つインレイトポプロットを表示します。 `positions` が必要です。
  * `topopositions_to_color::x -> pos_to_color_RomaO(x)`   ラインの色を変更します。
  * `topo_axis::NamedTuple = (;)`   ここでトポプロット軸の設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで `?Axis` と入力してください。   デフォルト: (width = GridLayoutBase.Relative(0.35f0), height = GridLayoutBase.Relative(0.35f0), halign = 0.05, valign = 0.95, aspect = 1)
  * `topo_attributes::NamedTuple = (;)`   ここでトポプロットの補間設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで `?Topoplot.topoplot` と入力してください。   デフォルト: (head = (color = :black, linewidth = 1), label_scatter = (markersize = 10, strokewidth = 0.5), interpolation = TopoPlots.NullInterpolator())
  * `mapping = (;)`   特定のチャネルを強調表示するためのもの。   例: `mapping = (; color = :highlight))`、ここで `:highlight` は適切なマッピングを持つ変数です。

**戻り値:** バタフライプロットを表示する `Figure`。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトがサイクルされて一致するまで続きます。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "時間", ylabel = "電圧 [µV]", yticklabelsize = 14, xtickformat = "{:.1f}") - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = false, use*colorbar = true, use*legend = true, hidespines = (:r, :t), hidedecorations = Dict{Symbol, Bool}(:label => 0, :ticks => 0, :ticklabels => 0)) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how*to/hide_deco/) を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y), color = (:channel, :channels, :trial, :trials), positions = (:pos, :positions, :position, :topo_positions, :x, nothing), labels = (:labels, :label, :topoLabels, :sensor, nothing), group = (:channel,)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) から任意のマッピングを使用してください* 

**visual =** (colormap = nothing, color = nothing) - *[`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/) の `kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, framevisible = false) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "", flipaxis = true) - *[`AlgebraOfGraphics.colorbar!`](@ref) の `kwargs...` を使用してください* 

さらに [`plot_erp`](@ref erp_vis) を参照してください
