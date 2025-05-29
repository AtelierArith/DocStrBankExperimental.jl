```
plot_designmatrix!(f::Union{GridPosition, GridLayout, Figure}, data::Unfold.DesignMatrix; kwargs...)
plot_designmatrix(data::Unfold.DesignMatrix; kwargs...)
```

デザインマトリックスをプロットします。

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための `Figure`、`GridLayout`、または `GridPosition`。
  * `data::Unfold.DesignMatrix`   プロットの視覚化のためのデータ。

## キーワード引数 (kwargs)

  * `standardize_data::Bool = false`   データがサンプル標準偏差での点ごとの除算によって標準化されるかどうかを示します。
  * `sort_data::Bool = false`   データがソートされているかどうかを示します。Base Juliaの `sortslices()` を使用します。
  * `xticks::Num = nothing`   x軸に表示されるラベルの数を指定します。

      * `xticks = 0`: ラベルは表示されません。
      * `xticks = 1`: 最初のラベルのみが表示されます。
      * `xticks = 2`: 最初と最後のラベルが表示されます。
      * `2 < xticks < ラベルの数`: ラベルは軸に均等に分配されます。
      * `xticks ≥ ラベルの数`: すべてのラベルが表示されます。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトがサイクルされて一致するまで続きます。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "条件", ylabel = "試行", xticklabelrotation = 0.39) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/) を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) から任意のマッピングを使用してください* 

**visual =** (colormap = :roma,) - *[`Makie.heatmap`](https://docs.makie.org/stable/reference/plots/heatmap/) の `kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "") - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/) の `kwargs...` を使用してください* 

**戻り値:** デザインマトリックスを表示する `Figure`。 
