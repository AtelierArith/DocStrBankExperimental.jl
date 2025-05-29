```
initstate!(mpc::PredictiveController, u, ym, d=[]) -> x̂
```

`mpc.estim` [`StateEstimator`](@ref) の状態を初期化し、`mpc.Z̃` をゼロでウォームスタートします。

また、入力の増分 $\mathbf{ΔU}$ を入力 $\mathbf{U}$ に変換するために、`mpc.lastu0` に `u - mpc.estim.model.uop` を保存します。
