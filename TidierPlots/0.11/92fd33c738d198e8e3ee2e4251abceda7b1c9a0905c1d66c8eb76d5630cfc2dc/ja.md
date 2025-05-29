```
geom_step(aes(...), ...)
geom_step(plot::GGPlot, aes(...), ...)
```

データを階段状のプロットとして表現します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.Stairsに渡される)

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

ggplot(df, @aes(x = x, y = y)) + geom_step()
```
