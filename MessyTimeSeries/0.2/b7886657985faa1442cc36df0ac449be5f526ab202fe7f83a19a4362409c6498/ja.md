```
SizedKalmanStatus(R::SymMatrix, T::Int64)
SizedKalmanStatus(R::UniformScaling{Float64}, T::Int64)
SizedKalmanStatus(settings::KalmanSettings)
```

初期化された `SizedKalmanStatus` 構造体を返します。 `R` はカルマンフィルタとスムーザーの通常 / 逐次実装のために構造体を特化させます。
