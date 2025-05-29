```
geom_line(aes(...), ...)
geom_line(plot::GGPlot, aes(...), ...)
```

x軸の変数の順序で接続された点としてデータを表します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列の名前
  * `...`: 列にマッピングされていないオプション (Makie.Linesに渡される)

# 必須の美的要素

  * `x`
  * `y`

# オプションの美的要素 (参照 [`aes`](@ref))

  * `color` / `colour`

# オプションの引数

  * `color` / `colour`
  * `colormap` / `palette`
  * `linestyle` / `linetype`
  * `linewidth`
  * `alpha`

# 例

```julia
xs = range(0, 2pi, length=30)
df = DataFrame(x = xs, y = sin.(xs))

ggplot(df, @aes(x = x, y = y)) + geom_line()
```
