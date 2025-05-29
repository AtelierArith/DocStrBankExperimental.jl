```
normalized_laplacian(g, [T=float(eltype(g))]; dir=:both, selfloop=false)
```

グラフ `g` の正規ラプラシアン行列は次のように定義されます。

$$
I - D^{-\frac{1}{2}} \tilde{A} D^{-\frac{1}{2}}
$$

ここで、$D$ は次数行列、$\tilde{A}$ は `g` からの自己ループのない隣接行列です。

# 引数

  * `g`: 隣接行列、`FeaturedGraph`、`SimpleGraph`、`SimpleDiGraph`（Graphsから）または `SimpleWeightedGraph`、`SimpleWeightedDiGraph`（SimpleWeightedGraphsから）である必要があります。
  * `T`: 結果の次数ベクトルの要素型。デフォルトの型は `g` の要素型です。
  * `dir::Symbol`: グラフ `g` の次数をその方向に関して計算する方法。`:in`、`:out`、または `:both` である必要があります。
  * `selfloop::Bool`: $\tilde{A}$ に自己ループを追加するかどうか。
