```
geom_density(aes(...), ...)
geom_density(plot::GGPlot, aes(...), ...)
```

データを滑らかな密度曲線として表現します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.Densityに渡される)

# 必須の美学

  * `x`

# オプションの美学 (参照 [`aes`](@ref))

  * NA

# オプションの引数

  * `color` / `colour`
  * `colormap` / `palette`
  * `strokecolor` / `strokecolour`
  * `strokewidth` / `stroke`
  * `linestyle` / `linetype`
  * `direction=:x`
  * `npoints=200`

# 例

```julia
ggplot(penguins, @aes(x=bill_length_mm)) + geom_density()

ggplot(penguins, @aes(x=bill_length_mm)) +
    geom_density(color = :black, stroke = 2)
```
