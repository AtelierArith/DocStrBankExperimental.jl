```
latent_heat_liq_ice(param_set, q::PhasePartition{FT})
```

凝縮物の有効潜熱（液体と氷の加重平均）、基準温度 `T_0` で評価された特定の潜熱が与えられます。

  * `param_set` は `AbstractParameterSet` であり、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
