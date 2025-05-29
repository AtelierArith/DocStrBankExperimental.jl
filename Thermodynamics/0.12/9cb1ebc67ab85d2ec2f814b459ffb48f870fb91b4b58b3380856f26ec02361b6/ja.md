```
internal_energy_sat(param_set, T, ρ, q_tot, phase_type)
```

飽和状態における熱平衡での単位質量あたりの内部エネルギーは次のように定義されます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` は温度
  * `ρ` は（湿った）空気の密度
  * `q_tot` は総比湿度
  * `phase_type` は熱力学的状態のタイプ
