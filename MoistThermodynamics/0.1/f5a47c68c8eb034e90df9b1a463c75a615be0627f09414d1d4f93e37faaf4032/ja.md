```
air_temperature_from_liquid_ice_pottemp_non_linear(θ_liq_ice, ρ, q::PhasePartition)
```

液体氷のポテンシャル温度 `θ_liq_ice`、(湿)空気密度 `ρ`、非線形方程式解法のための許容誤差 `tol`、非線形方程式解法のための最大反復回数 `maxiter` を与えられたときに温度 `T` を計算します。

オプションとして、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。

$$
T - air_temperature_from_liquid_ice_pottemp_given_pressure(θ_liq_ice, air_pressure(T, ρ, q), q) = 0
$$

の根を見つけることによって。
