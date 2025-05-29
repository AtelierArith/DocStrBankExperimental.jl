```
get_zero_draws(covar::ForwardCovariance)
```

すべての `ItoIntegral` に対してゼロのドローを取得します。これはバグハンティングに便利かもしれません。

### 入力

  * covar - ゼロドローを取得したい `ForwardCovariance` 構造体

### 出力

  * ゼロドローの `Dict`
