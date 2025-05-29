```
make_nan_covariance_matrix(
    labels::Vector{Symbol},
    time_period_per_unit::Dates.Period,
)
```

これは、すべてのボラティリティと相関がNaNである空の`CovarianceMatrix`構造体を作成します。

### 入力

  * `labels` - この（空の）`CovarianceMatrix`の資産名の名前。
  * `time_period_per_unit` - ボラティリティの時間間隔。

### 返り値

  * （空の）`CovarianceMatrix`
