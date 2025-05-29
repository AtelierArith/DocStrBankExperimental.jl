```
liquid_ice_pottemp_sat(param_set, T, ρ, phase_type[, q::PhasePartition, cpm])
```

飽和液体氷のポテンシャル温度は次のように定義されます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `T` は温度です。
  * `ρ` は（湿った）空気の密度です。
  * `phase_type` は熱力学的状態のタイプです。

オプションとして、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
