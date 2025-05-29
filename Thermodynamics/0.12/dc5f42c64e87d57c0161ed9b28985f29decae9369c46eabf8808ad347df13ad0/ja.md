```
PhaseEquil_ρθq(param_set, ρ, θ_liq_ice, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

[`PhaseEquil`](@ref) 熱力学状態を次のように構築します：

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `ρ` （湿った）空気の密度
  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `q_tot` 総特定湿度
  * `relative_temperature_tol` 飽和調整のための相対温度許容範囲
  * `maxiter` 飽和調整のための最大反復回数
  * `T_guess` 飽和調整における温度の初期推定値
