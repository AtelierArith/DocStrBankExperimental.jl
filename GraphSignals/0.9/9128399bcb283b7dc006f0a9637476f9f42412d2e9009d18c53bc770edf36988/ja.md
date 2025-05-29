```
laplacian_matrix(g, [T=eltype(g)]; dir=:out)
```

グラフ `g` のラプラシアン行列は次のように定義されます。

$$
D - A
$$

ここで、$D$ は次数行列、$A$ は `g` からの隣接行列です。

# 引数

  * `g`: 隣接行列、`FeaturedGraph`、`SimpleGraph`、`SimpleDiGraph`（Graphsから）または `SimpleWeightedGraph`、`SimpleWeightedDiGraph`（SimpleWeightedGraphsから）である必要があります。
  * `T`: 結果の次数ベクトルの要素型。デフォルトの型は `g` の要素型です。
  * `dir::Symbol`: グラフ `g` の次数をその方向に関して計算する方法。`:in`、`:out`、または `:both` である必要があります。
