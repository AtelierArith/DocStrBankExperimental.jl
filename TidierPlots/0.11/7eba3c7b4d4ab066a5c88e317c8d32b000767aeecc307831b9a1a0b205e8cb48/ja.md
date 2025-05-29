```
geom_histogram(aes(...), ...)
geom_histogram(plot::GGPlot, aes(...), ...)
```

データをヒストグラムとして表現します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.Histに渡される)

# 必須の美的要素

  * `x`

# オプションの美的要素 (参照 [`aes`](@ref))

  * NA

# オプションの引数

  * `bins`
  * `normalization`
  * `color` / `colour`
  * `stroke` / `strokewidth`
  * `strokecolor` / `strokecolour`

# 例

```julia
ggplot(penguins, @aes(x = bill_length_mm)) +
    geom_histogram()

ggplot(penguins, @aes(x = bill_length_mm)) +
    geom_histogram(normalization=:probability, bins=20)
```
