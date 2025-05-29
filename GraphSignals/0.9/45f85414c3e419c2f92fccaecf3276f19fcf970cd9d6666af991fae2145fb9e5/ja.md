```
scaled_laplacian(g, [T=float(eltype(g))])
```

スケーリングされたラプラシアン行列 `g` のグラフで、次のように定義されます。

$$
\hat{L} = \frac{2}{\lambda_{max}} \tilde{L} - I
$$

ここで、$\tilde{L}$ は正規化されたラプラシアン行列です。

# 引数

  * `g`: 隣接行列、`FeaturedGraph`、`SimpleGraph`、`SimpleDiGraph`（Graphsから）または `SimpleWeightedGraph`、`SimpleWeightedDiGraph`（SimpleWeightedGraphsから）である必要があります。
  * `T`: 結果の次数ベクトルの要素型。デフォルトの型は `g` の要素型です。
