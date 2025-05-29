```
initstate!(mpc::PredictiveController, u, ym, d=[]) -> x̂
```

`mpc.estim` [`StateEstimator`](@ref) の状態を初期化し、`mpc.Z̃` をゼロでウォームスタートします。
