```
virtual_temperature(param_set, T[, q::PhasePartition])
```

仮想温度は次のとおりです。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `T` は温度です。

そして、オプションで、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
