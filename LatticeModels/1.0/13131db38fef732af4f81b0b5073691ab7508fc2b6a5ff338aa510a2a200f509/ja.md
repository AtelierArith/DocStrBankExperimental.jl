```
kanemele(lat, t1, t2[; T, μ, field, statistics])
```

$$
\hat{H} = \sum_{i, j}^\text{adjacent} \left( t_1 c^\dagger_i c_j + h. c. \right) + \sum_{i, j}^\text{2-connected, counter-clockwise} \left( i \cdot t_2 c^\dagger_i σ_z c_j + h. c. \right)
$$

与えられた格子 `lat` 上にケイン-メレハミルトニアン演算子を生成します。

## キーワード引数

  * `T`: 系の温度。デフォルトはゼロです。
  * `μ`: 化学ポテンシャル。Unicode入力が利用できない場合は、同義語としてキーワード `mu` を使用してください。
  * `field`: 磁場。デフォルトは `NoField()` です。
  * `statistics` は粒子統計を定義します。`FermiDirac` または `BoseEinstein` のいずれかです。
