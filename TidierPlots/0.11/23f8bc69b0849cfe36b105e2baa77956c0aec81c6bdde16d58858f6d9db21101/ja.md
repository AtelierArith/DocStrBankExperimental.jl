```
geom_bar(aes(...), ...)
geom_bar(plot::GGPlot, aes(...), ...)
```

グループ化変数のカウントを列として表現します。

# 詳細

列はデフォルトでスタックされ、"position" 引数で動作を変更できます。位置は "stack" または "dodge" のいずれかです。引数が "dodge" の場合、`aes` にグループ化変数を供給する必要があります。あるいは、美的表現内で `dodge` にグループ化変数を供給することもできます。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるデータフレームの列名
  * `...`: 列にマッピングされていないオプション (Makie.BarPlot に渡される)

# 必須の美的表現

  * `x` または `y` (両方ではない)

# オプションの美的表現 (見てください [`aes`](@ref))

  * `color` / `colour`
  * `strokecolor` / `strokecolour`
  * `dodge`
  * `group`

# オプションの引数

  * `position`: "stack" (デフォルト) または "dodge"
  * `stroke` / `strokewidth`
  * `strokecolor` / `strokecolour`
  * `direction`: `:y` (デフォルト) または :x
  * `dodge_gap`
  * `gap`

# 例

```julia
# 縦棒グラフ
ggplot(penguins) + geom_bar(@aes(x = species))

# 横棒グラフ
ggplot(penguins) + geom_bar(@aes(y = species))

# スタック
ggplot(penguins, @aes(x = species, fill=sex)) + geom_bar()

# ドッジ
ggplot(penguins, @aes(x = species, fill=sex, dodge = sex)) + geom_bar()
```
