```
PhaseEquil_ρeq(param_set, ρ, e_int, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

湿潤熱力学的相、次の条件に基づいて

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `ρ` 密度
  * `e_int` 内部エネルギー
  * `q_tot` 総特定湿度

および、オプションで

  * `maxiter` 飽和調整の最大反復回数
  * `relative_temperature_tol` 飽和調整のための相対温度許容範囲
  * `sat_adjust_method` 使用する数値的方法。オプションについては [`Thermodynamics`](@ref) を参照してください。
  * `T_guess` 飽和調整における温度の初期推定値
