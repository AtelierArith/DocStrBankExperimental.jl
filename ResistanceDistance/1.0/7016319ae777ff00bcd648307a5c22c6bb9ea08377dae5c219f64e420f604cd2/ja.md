```
resistance_distance(g, i::Int64, j::Int64)
```

グラフ内の2つのノード間の抵抗距離を計算します。

# 引数

  * `g`: 抵抗距離を計算するグラフ。
  * `i`: 最初のノード。
  * `j`: 2番目のノード。

# 戻り値

  * ノード `i` と `j` の間の抵抗距離。

# 注意事項

  * 実装:

Bapat, Ravindra B., Gutmana, Ivan and Xiao, Wenjun. "A Simple Method for Computing Resistance Distance" Zeitschrift für Naturforschung A, vol. 58, no. 9-10, 2003, pp. 494-498. https://doi.org/10.1515/zna-2003-9-1003
