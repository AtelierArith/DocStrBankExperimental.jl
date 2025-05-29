```
geom_errorbarh(aes(...), ...)
geom_errorbarh(plot::GGPlot, aes(...), ...)
```

データを水平の区間として表現します。

# 引数

  * `plot::GGPlot`（オプション）: このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション（Makie.Rangebarsに渡される）

# 必須の美的要素

  * `y`
  * `xmin`
  * `xmax`

# オプションの美的要素（[`aes`](@ref)を参照）

  * NA

# オプションの引数

  * `color` / `colour`
  * `direction=:x`
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

ggplot(df, @aes(y = trt, xmin = lower, xmax = upper)) +
    geom_errorbarh(linewidth=2)
```
