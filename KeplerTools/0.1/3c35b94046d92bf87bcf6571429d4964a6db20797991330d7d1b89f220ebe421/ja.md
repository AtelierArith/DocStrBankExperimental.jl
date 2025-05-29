```
v̄ = orbital_velocity(θ, a, e, μ, basis)
v̄ = orbital_velocity(θ, a, e, μ, i, Ω, ω)
v̄ = orbital_velocity(θ, orbit)
```

真異常 `θ` における速度ベクトルを、半長軸 `a`、離心率 `e`、重力定数 `μ`、および軌道のペリフォーカル平面を定義する回転 `basis` を用いて計算します。

回転は、傾斜 `i`、RAAN `Ω`、および近点引数 `ω` から計算できます。
