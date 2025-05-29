```
geom_smooth(aes(...), ...)
geom_smooth(plot::GGPlot, aes(...), ...)
```

データを平滑化または線形フィットとして表現します。

# 引数

  * `plot::GGPlot`（オプション）：このジオムを追加するプロットオブジェクト
  * `aes(...)`：マッピングに使用されるDataFrameの列の名前
  * `...`：列にマッピングされていないオプション（Makie.Linesに渡される）

# 必須の美的要素

  * `x`
  * `y`

# オプションの美的要素（[`aes`](@ref)を参照）

  * NA

# オプションの引数

  * `method`： "smooth"（デフォルト、loessフィット）または "lm"（線形フィット）
  * `color` / `colour`
  * `linewidth`
  * `alpha`
  * `linestyle` / `linetype`

# 例

```julia
xs = range(0, 2pi, length=30)
ys = sin.(xs) .+ randn(length(xs)) * 0.5
df = DataFrame(x = xs, y = ys)

ggplot(df, @aes(x = x, y = y)) + geom_smooth() + geom_point()

ggplot(penguins, @aes(x = bill_length_mm, y = bill_depth_mm)) +
    geom_smooth(color=:red, linewidth=10, alpha=0.5)
```
