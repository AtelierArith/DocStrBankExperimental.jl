```
geom_hline(aes(...), ...)
geom_hline(plot::GGPlot, aes(...), ...)
```

指定された y 切片で水平線をプロットします。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用される DataFrame の列の名前
  * `...`: 列にマッピングされていないオプション (Makie.HLines に渡される)

# 必要な美学

  * NA

# オプションの美学 (参照 [`aes`](@ref))

  * `yintercept(s)`
  * `color` / `colour`

# オプションの引数

  * `yintercept(s)`
  * `color` / `colour`
  * `linewidth`
  * `linestyle` / `linetype`
  * `colormap` / `palette`
  * `alpha`

# 例

```julia
# 単一の y 切片のみをプロット
ggplot() + geom_hline(yintercept = 3)

# 複数の y 切片をプロット
ggplot() + geom_hline(yintercept = [-1, 4])

# 列にマッピングされた複数の y 切片をプロット
df = DataFrame(y = rand(4))
ggplot(df, @aes(yintercept = y)) + geom_hline()
```
