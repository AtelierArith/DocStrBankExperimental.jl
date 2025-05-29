```
PhaseNonEquil_ρθq(param_set, ρ, θ_liq_ice, q_pt)
```

[`PhaseNonEquil`](@ref) 熱力学状態を次のように構築します：

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `ρ` （湿った）空気の密度
  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `q_pt` 相の分配

および、オプションで

  * `relative_temperature_tol` 非線形方程式解法のためのポテンシャル温度
  * `maxiter` 非線形方程式解法のための最大反復回数
