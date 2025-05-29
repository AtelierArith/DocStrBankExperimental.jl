```
get_volatility(
    covar::CovarianceMatrix,
    asset1::Symbol,
    time_period_per_unit::Dates.Period = covar.time_period_per_unit,
)
```

`CovarianceMatrix`から株式のボラティリティを取得します。

### 入力

  * `covar` - `CovarianceMatrix`
  * `asset1` - 資産を表す`Symbol`。
  * `time_period_per_unit` - ボラティリティの時間間隔。

### 返り値

  * スカラー（ボラティリティ）。
