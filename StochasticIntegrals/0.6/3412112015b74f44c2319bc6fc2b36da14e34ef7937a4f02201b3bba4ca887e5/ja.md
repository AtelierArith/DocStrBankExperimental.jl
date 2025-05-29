```
volatility(covar::ForwardCovariance, index::Integer, on::Union{Date,DateTime})
volatility(covar::ForwardCovariance, id::Symbol, on::Union{Date,DateTime})
```

`ForwardCovariance` のボラティリティを日付で取得します。

### 入力

  * `covar` - ボラティリティを取得したい `ForwardCovariance`。
  * `index` - 興味のあるito辞書のキー。
  * `on` - ボラティリティを取得したい時間または瞬間。

### 戻り値

  * スカラー
