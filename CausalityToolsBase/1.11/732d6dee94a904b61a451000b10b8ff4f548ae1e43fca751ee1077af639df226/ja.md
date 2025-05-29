```
RefinedTriangulationBinningSplitQuantile
```

三角形単体分割のためのビニングスキームで、いくつかの単体が洗練されている（形状を保持する単体分割アルゴリズムによって細分化されている）三角形単体パーティションです。

分割比率の制約は、初期の三角形単体の各単体がどれだけ分割されるかを制御します。

## フィールド

  * **`split_quantile::Float64`**: 半径が初期三角形単体の半径の `split_quantile`-分位数より大きいすべての単体は、`simplex_split_factor` の分割係数で分割されます。
  * **`simplex_split_factor::Int`**: 各単体が分割される回数。
