```
PhaseEquil_peq(param_set, p, e_int, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

温度から[`PhaseEquil`](@ref)熱力学状態を構築します。

  * `param_set`は`AbstractParameterSet`で、詳細については[`Thermodynamics`](@ref)を参照してください
  * `p`は圧力
  * `e_int`は温度
  * `q_tot`は総特定湿度
  * `T_guess`は飽和調整における温度の初期推測
