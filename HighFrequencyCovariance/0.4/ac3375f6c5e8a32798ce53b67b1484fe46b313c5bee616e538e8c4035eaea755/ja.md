```
rearrange(
    cm::CovarianceMatrix,
    labels::Vector{Symbol},
    time_period_per_unit::Union{Missing,Dates.Period} = cm.time_period_per_unit,
)
```

`CovarianceMatrix`内のラベルの順序を再配置します。

### 引数

  * `cm` - `CovarianceMatrix`。
  * `labels` - ラベルの`Vector`。
  * `time_period_per_unit` - 結果の共分散行列に対して希望する時間の期間。

### 戻り値

  * `CovarianceMatrix`。
