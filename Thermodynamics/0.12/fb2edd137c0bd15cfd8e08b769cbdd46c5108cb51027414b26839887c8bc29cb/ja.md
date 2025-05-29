```
gas_constant_air(param_set, [q::PhasePartition])
```

湿った空気の特定の気体定数は次のように与えられます

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
