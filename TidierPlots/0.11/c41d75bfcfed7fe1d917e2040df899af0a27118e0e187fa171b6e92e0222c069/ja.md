```
geom_boxplot(aes(...), ...)
geom_boxplot(plot::GGPlot, aes(...), ...)
```

連続データの分布を簡潔に表示します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.BoxPlotに渡される)

# 必須の美的要素

  * `x` (整数またはカテゴリカル)
  * `y` (数値)

# オプションの美的要素 ( [`aes`](@ref) を参照)

  * `color` / `colour` ( `dodge` と併用)
  * `dodge`

# オプションの引数

  * `orientation=:vertical`: ボックスの向き (`:vertical` または `:horizontal`)
  * `width=1`
  * `gap=0.2`
  * `show_notch=false`
  * `nothchwidth=0.5`
  * `show_median=true`
  * `dodge_gap=0.03`

# 例

```julia
ggplot(penguins, @aes(x=species, y=bill_length_mm)) +
    geom_boxplot()

ggplot(penguins, @aes(y=species, x=bill_length_mm)) +
    geom_boxplot()

ggplot(penguins, @aes(x=species, y=bill_length_mm, fill=sex)) +
    geom_boxplot()
```
