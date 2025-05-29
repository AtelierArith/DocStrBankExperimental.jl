```
qwz(m[; T, μ, field, statistics])
qwz(lat[, m; T, μ, field, statistics])
```

$$
\hat{H} = \sum_i^\text{sites} m_i c^\dagger_i \sigma_z c_i + \sum_i^\text{sites} \left( c^\dagger_{i + \hat{x}} \frac{\sigma_z - i \sigma_x}{2} c_i + c^\dagger_{i + \hat{y}} \frac{\sigma_z - i \sigma_y}{2} c_i + h. c. \right)
$$

与えられた正方格子 `lat` 上に QWZ モデルハミルトニアン演算子を生成します。

## 引数

  * `m`（`LatticeValue` または数値）は $m_i$ 因子を定義します。

## キーワード引数

  * `T`: 系の温度。デフォルトはゼロです。
  * `μ`: 化学ポテンシャル。Unicode 入力が利用できない場合は `mu` を同義語として使用してください。
  * `field`: 磁場。デフォルトは `NoField()` です。
  * `statistics` は粒子統計を定義します。`FermiDirac` または `BoseEinstein` のいずれかです。
