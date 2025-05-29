```
get_zero_draws(covar::ForwardCovariance, num::Integer)
```

すべての `ItoIntegral` のゼロドローの配列を取得します。バグハンティングに便利かもしれません。

### 入力

  * `covar` - ゼロドローを取得したい `ForwardCovariance` 構造体
  * `num` - 取得したいゼロドローの数。

### 出力

  * ゼロドローの `Dict` の `Vector`
