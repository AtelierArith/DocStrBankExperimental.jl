```
plot_splines(m::UnfoldModel; kwargs...)
plot_splines!(f::Union{GridPosition, GridLayout, Figure}, m::UnfoldModel; kwargs...)
```

UnfoldModelにおけるスプライン項の視覚化。各スプライン項について2つのサブプロットが生成されます：

1. スプラインの基底関数；2) 基礎となる共変量の密度。

複数のスプライン項が列に配置されます。 破線はスプラインノットを示します。

## 引数：

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための`Figure`、`GridLayout`、または`GridPosition`。
  * `m::UnfoldModel`   スプラインを持つUnfoldModel。
  * `spline_axis::NamedTuple = (;)`   ここでスプラインサブプロットの設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで`?Axis`と入力してください。   デフォルト： (ylabel = "スプライン値", xlabelvisible = false, xticklabelsvisible = false, ylabelvisible = true)
  * `density_axis::NamedTuple = (;)`   ここで密度サブプロットの設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで`?Axis`と入力してください。   デフォルト： (xautolimitmargin = (0, 0), ylabel = "密度値")
  * `superlabel_config::NamedTuple = (;)`   ここでプロットの上部にあるラベルの設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで`?Label`と入力してください。   デフォルト： (fontsize = 20, padding = (0, 0, 40, 0))

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます： `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "テスト"))`。 複数のデフォルトが一致するまで循環します。

`;`を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)の`kwargs...`を使用してください* 

**axis =** NamedTuple() - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)の`kwargs...`を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この[ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)から任意のマッピングを使用してください* 

**visual =** (colormap = :viridis,) - *[`Makie.series`](https://docs.makie.org/stable/reference/plots/series)の`kwargs...`を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, title = "スプライン", framevisible = false) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)の`kwargs...`を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)の`kwargs...`を使用してください* 

**戻り値：** 基底関数のスプラインとその密度を持つ`Figure`。
