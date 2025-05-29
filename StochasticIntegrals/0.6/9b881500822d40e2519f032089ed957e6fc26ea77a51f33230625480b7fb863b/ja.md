```
get_draws(covar::ForwardCovariance; uniform_draw::Array{T,1} = rand(length(covar.covariance_labels_))) where T<:Real
```

### 入力

  * `covar` - 引き出したい `ForwardCovariance` または `SimpleCovariance` 構造体。
  * `uniform_draw` - 一様分布からの引き出しベクトル。

### 戻り値

  * 引き出しの辞書。
