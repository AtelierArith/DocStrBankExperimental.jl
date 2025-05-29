```
SmootherOutput{NamedTuple}
```

Quadratic Kalman Smootherからの出力のコンテナ。

# フィールド

  * `Z_smooth::Matrix{T}`: スムーズ化された状態 (P × (T̄+1))
  * `P_smooth::Array{T,3}`: スムーズ化された共分散 (P × P × (T̄+1))
