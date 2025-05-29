```
geom_path(aes(...), ...)
geom_path(plot::GGPlot, aes(...), ...)
```

データをデータ内に現れる順序で接続されたポイントとして表現します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列の名前
  * `...`: 列にマッピングされていないオプション (Makie.Linesに渡される)

# 必須の美的要素

  * `x`
  * `y`

# オプションの美的要素 (see [`aes`](@ref))

  * `color` / `colour`

# オプションの引数

  * `color` / `colour`
  * `colormap` / `palette`
  * `linestyle` / `linetype`
  * `linewidth`
  * `alpha`

# 例

```julia
ggplot(penguins, @aes(x = bill_length_mm, y = bill_depth_mm)) +
    geom_path()
```
