```
boundary_conditions_new(P::Float64, T::Float64, V::Float64, rho_m::Float64, rho_x::Float64, c::Float64, sw::SW{Int8}, T_in::Float64, M_h2o::Float64, M_co2::Float64, total_Mass::Float64, param::Param{Float64}, param_saved_var::ParamSaved{Float64})
```

## 引数

  * `P`: 圧力 (Pa)
  * `T`: 温度 (K)
  * `V`: チャンバーの体積 (m³)
  * `rho_m`: 溶融物の密度
  * `rho_x`: マグマの結晶の密度
  * `c`: マグマの熱
  * `sw`: 噴火/冷却*モジュール/粘性*緩和制御
  * `T_in`: 温度
  * `M_h2o`: マグマ中のH2Oの総質量
  * `M_co2`: マグマ中のCO2の総質量
  * `total_Mass`: マグマチャンバーの総質量
