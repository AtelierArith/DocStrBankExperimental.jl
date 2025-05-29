```
r̄, v̄ = state_vector(θ, a, e, μ, basis)
r̄, v̄ = state_vector(θ, a, e, μ, i, Ω, ω)
r̄, v̄ = state_vector(θ, orbit)
```

真異常 `θ` における状態ベクトルを、半長軸 `a`、離心率 `e`、重力定数 `μ`、および軌道のペリフォーカル平面を定義する回転 `basis` を用いて計算します。

回転は、傾斜 `i`、RAAN `Ω`、および近点引数 `ω` から計算できます。
