```
geom_col(aes(...), ...)
geom_col(plot::GGPlot, aes(...), ...)
```

データを列として表現します。

# 詳細

列はデフォルトでスタックされ、"position" 引数で動作を変更できます。位置は "stack" または "dodge" のいずれかです。引数が "dodge" の場合、`aes` にグループ化変数を供給する必要があります。あるいは、美的表現内で `dodge` にグループ化変数を供給することもできます。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列名
  * `...`: 列にマッピングされていないオプション (Makie.BarPlotに渡される)

# 必須美的表現

  * `x`
  * `y`

# オプションの美的表現 (see [`aes`](@ref))

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
df = @chain penguins begin
    @group_by(species, sex)
    @summarize(mean_bill_length_mm = mean(bill_length_mm))
    @ungroup()
end

ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm))

# グループと位置引数を使用してドッジ
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, group = sex),
             position="dodge")

# ドッジ美的表現を使用
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, dodge = sex))

# グループ化変数に基づく色
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, color = sex))
```
