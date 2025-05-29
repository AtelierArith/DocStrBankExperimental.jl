```
plot_parallelcoordinates(data::Union{DataFrame, AbstractMatrix}; kwargs...)
plot_parallelcoordinates!(f::Union{GridPosition, GridLayout, Figure}, data::Union{DataFrame, AbstractMatrix}; kwargs)
```

PCP（平行座標プロット）をプロットします。 次元：条件、チャネル、時間、試行。

## 引数：

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための`Figure`、`GridLayout`、または`GridPosition`。
  * `data::Union{DataFrame, AbstractMatrix}`   プロットの視覚化のためのデータ。

## キーワード引数（kwargs）

  * `normalize::Symbol = nothing`   `:minmax`の場合、各軸をそれぞれの最小-最大範囲に正規化します。
  * `ax_labels::Vector{String} = nothing`   軸ラベルを指定します。   ユニークな`mapping.x`の値の数と同じ長さのラベルのベクターである必要があります。   例：`ax_labels = ["Fz", "Cz", "O1", "O2"]`。
  * `ax_ticklabels::Symbol = :outmost`   軸の目盛りラベルを指定します。

      * `:all` - すべての軸にすべてのラベルを表示します。
      * `:left` - 左の軸にすべてのラベルを表示し、他の軸には最小と最大のみを表示します。
      * `:outmost` - 他のすべての軸の最小と最大にラベルを表示します。
      * `:none` - すべてのラベルを削除します。
  * `bend::Bool = false`   軸間の直線を曲線（「曲がった」）に変更します。スプライン補間を使用します。   注意：これによりプロットがかっこよく見えますが、一般的には線を曲げることは推奨されません。解釈が損なわれ、結果として得られる視覚化が誤解を招く可能性があります。
  * `visual.alpha::Number = 0.5`   線の透明度を変更します。

## 軸の定義

  * `mapping.x = :channel, mapping.y = :estimate`。   x軸とy軸に何を表示するかを上書きします。
  * `mapping.color = :colorcolumn`    条件を色で分割します。デフォルトの色は`:black`です。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます：`type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトが循環して一致するまで続きます。

`;`を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)の`kwargs...`を使用してください* 

**axis =** (xlabel = "Channels", ylabel = "Time", title = "", xlabelpadding = 14, ylabelpadding = 26) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)の`kwargs...`を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この[ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/)を確認してください* 

**mapping =** (x = :channel, y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)から任意のマッピングを使用してください* 

**visual =** (colormap = ColorTypes.RGBA{Float32}[RGBA(0.0, 0.44705883, 0.69803923, 1.0), RGBA(0.9019608, 0.62352943, 0.0, 1.0), RGBA(0.0, 0.61960787, 0.4509804, 1.0), RGBA(0.8, 0.4745098, 0.654902, 1.0), RGBA(0.3372549, 0.7058824, 0.9137255, 1.0), RGBA(0.8352941, 0.36862746, 0.0, 1.0), RGBA(0.9411765, 0.89411765, 0.25882354, 1.0)], color = :black, alpha = 0.3) - *[`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)の`kwargs...`を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, title = "Conditions", merge = true, framevisible = false) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)の`kwargs...`を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966) - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/)の`kwargs...`を使用してください* 

**戻り値：** `Figure` 平行座標プロットを表示します。
