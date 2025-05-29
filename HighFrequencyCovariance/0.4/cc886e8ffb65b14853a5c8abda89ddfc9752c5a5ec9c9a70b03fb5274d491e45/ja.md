```
covariance(
    cm::CovarianceMatrix,
    period::Dates.Period = cm.time_period_per_unit,
    assets::Vector{Symbol} = cm.labels,
)
```

これは、特定の期間にわたる共分散行列のための `Hermitian` 行列を作成します。

### 入力

  * `cm` - `CovarianceMatrix` 構造体。
  * `period` - 共分散行列を求める期間。この期間は Dates.Period である必要があります。
  * `assets` - 共分散行列に含める資産。

### 戻り値

  * `Hermitian`。各行/列の資産のラベリングは、入力された `assets` ベクターに従います。
