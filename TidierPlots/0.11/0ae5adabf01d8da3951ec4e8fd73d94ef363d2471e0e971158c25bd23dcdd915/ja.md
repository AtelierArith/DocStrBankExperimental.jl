```
geom_vline(aes(...), ...)
geom_vline(plot::GGPlot, aes(...), ...)
```

指定された y 切片で水平線をプロットします。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用される DataFrame の列名
  * `...`: 列にマッピングされていないオプション (Makie.VLines に渡される)

# 必要な美学

  * NA

# オプションの美学 (see [`aes`](@ref))

  * `xintercept(s)`
  * `color` / `colour`

# オプションの引数

  * `xintercept(s)`
  * `color` / `colour`
  * `linewidth`
  * `linestyle` / `linetype`
  * `colormap` / `palette`
  * `alpha`

# 例

```julia
# 単一の x 切片のみをプロット
ggplot() + geom_vline(xintercept = 3)

# 複数の x 切片をプロット
ggplot() + geom_vline(xintercept = [-1, 4])

# 列にマッピングされた複数の x 切片をプロット
df = DataFrame(x = rand(4))
ggplot(df, @aes(xintercept = x)) + geom_vline()
```
