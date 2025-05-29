```
bar(labels, heights; kwargs...)
bar(heights; kwargs...)
```

棒グラフを描画します。

特定のラベルが指定されていない場合、バーは1から始まる整数でラベル付けされます。

`heights`が行列の場合、各列は異なるデータセットとして扱われ、異なる色のバーで表されます。バーが横に並ぶか、前の系列の上に積み重ねられるかを制御するには、キーワード引数`barposition`に`"grouped"`（デフォルト）または`"stacked"`の値を使用します。

キーワード引数`barwidth`、`baseline`、および`horizontal`もバーの外観を変更するために使用できます。デフォルトは次のとおりです：

  * `barwidth = 0.8`（バー間の分離の80%）。
  * `baseline = 0.0`（バーはゼロから始まる）。
  * `horizontal = false`（垂直バー）

バーの色は自動的に選択されますが、特定の16進RGBカラーコードがキーワード引数`color`を通じて指定された場合はそれが使用されます。

# 例

```julia
# サンプルデータを作成（大陸の人口、百万単位）
continents = ["Africa", "America", "Asia", "Europe", "Oceania"]
population_1960 = [285, 425, 1687, 606, 16]
population_2010 = [1044, 944, 4170, 735, 36]
population_matrix = [population_1960 population_2010]
# 500百万の人々に対してプロット
barplot(continents, population_matrix, baseline=500)
legend("1960", "2010") # 凡例を追加
```
