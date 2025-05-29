```
geom_text(aes(...), ...)
geom_text(plot::GGPlot, aes(...), ...)
```

グラフにテキストをプロットします。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.Textに渡される)

# 必須の美的要素

  * `x`
  * `y`
  * `text`

# オプションの美的要素 (参照 [`aes`](@ref))

  * `color` / `colour`

# オプションの引数

  * `color` / `colour`
  * `colormap` / `palette`
  * `align`: 位置のタプル (例: `(:left, :bottom)`)
  * `font`
  * `justification`
  * `rotation`
  * `fontsize`
  * `strokewidth`
  * `strokecolor`
  * `glowwidth` / `glow`
  * `glowcolor` / `glowcolour`
  * `word_wrap_width`
  * `alpha`

# 例

```julia
df = DataFrame(
    x = [1,1,2,2],
    y = [1,2,1,2],
    t = ["A", "B", "C", "D"]
)

ggplot(df, @aes(x=x, y=y, text=t, color=t)) + geom_text()

ggplot(df, @aes(x=x, y=y, color=t)) +
    geom_text(@aes(text=t), fontsize=24, align=(:left, :bottom), font=:bold) +
    geom_point() +
    lims(x = (0, 3), y = (0, 3))
```
