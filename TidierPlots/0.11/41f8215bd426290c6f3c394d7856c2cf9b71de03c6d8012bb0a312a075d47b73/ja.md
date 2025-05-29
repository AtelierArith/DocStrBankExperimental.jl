```
geom_errorbar(aes(...), ...)
geom_errorbar(plot::GGPlot, aes(...), ...)
```

データを垂直の区間として表現します。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.Rangebarsに渡される)

# 必須の美的要素

  * `x`
  * `ymin`
  * `ymax`

# オプションの美的要素 ( [`aes`](@ref) を参照)

  * NA

# オプションの引数

  * `color` / `colour`
  * `direction=:y`
  * `linewidth`
  * `whiskerwidth` / `width`

# 例

```julia
df = DataFrame(
    trt   = [1, 1, 2, 2],
    resp  = [1, 5, 3, 4],
    group = [1, 2, 1, 2],
    lower = [0.8, 4.6, 2.4, 3.6],
    upper = [1.1, 5.3, 3.3, 4.2],
)

ggplot(df, @aes(x = trt, ymin = lower, ymax = upper)) +
    geom_errorbar(width=20, linewidth=2)
```
