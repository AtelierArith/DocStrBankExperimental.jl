```
air_pressure(param_set, T, ρ[, q::PhasePartition])
```

状態方程式（理想気体の法則）からの空気圧であり、

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` は空気の温度
  * `ρ` は（湿った）空気の密度

そして、オプションで、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
