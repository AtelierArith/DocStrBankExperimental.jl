```
internal_energy(param_set, T[, q::PhasePartition])
```

単位質量あたりの内部エネルギーは、熱力学的状態 `ts` に基づいています。または

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` は温度です

そして、オプションで、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
