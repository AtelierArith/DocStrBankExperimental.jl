```
r̄ = orbital_position(θ, a, e, basis)
r̄ = orbital_position(θ, a, e, i, Ω, ω)
r̄ = orbital_position(θ, orbit)
```

真異常 `θ` における位置ベクトルを、半長軸 `a`、離心率 `e`、および軌道のペリフォーカル平面を定義する回転 `basis` を持つ軌道のために計算します。

回転は、傾斜 `i`、RAAN `Ω`、および近点引数 `ω` から計算できます。
