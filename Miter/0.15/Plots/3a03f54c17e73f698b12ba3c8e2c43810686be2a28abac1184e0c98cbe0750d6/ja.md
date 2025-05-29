```julia
Plot(; ...)
Plot(contents; x_axis, y_axis, style, title)

```

与えられた `contents` でプロットを作成します（ベクターですが、複数の引数を受け入れる便利な形式も利用可能です）。

キーワード引数（デフォルト付き）:

  * `x_axis = Axis.Linear()`, `y_axis = Axis.Linear()`: x軸とy軸
  * `style = PlotStyle()`: プロットスタイル（例：マージン）
  * `title = nothing`: プロットのタイトル
