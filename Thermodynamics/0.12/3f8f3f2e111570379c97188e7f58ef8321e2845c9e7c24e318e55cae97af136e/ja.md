```
liquid_ice_pottemp_sat(param_set, T, ρ, phase_type, q_tot)
```

飽和液体氷のポテンシャル温度は次のように定義されます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` 温度
  * `ρ` （湿った）空気の密度
  * `phase_type` 熱力学的状態のタイプ
  * `q_tot` 総比湿度
