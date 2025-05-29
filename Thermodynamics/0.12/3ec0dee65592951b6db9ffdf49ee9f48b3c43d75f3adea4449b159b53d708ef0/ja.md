```
相分割_equil(param_set, T, ρ, q_tot, phase_type)
相分割_equil(param_set, T, ρ, q_tot, p_vap_sat, λ)
```

平衡状態の相を分割し、[`PhasePartition`](@ref) オブジェクトを返します。これは、[`liquid_fraction`](@ref) 関数を使用して行います。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `T` は温度です。
  * `ρ` は（湿った）空気の密度です。
  * `q_tot` は総比湿度です。
  * `phase_type` は熱力学的状態のタイプです。
  * `p_vap_sat` は飽和蒸気圧です。
  * `λ` は液体分率です。

残りの `q.tot - q.liq - q.ice` は蒸気の比湿度です。
