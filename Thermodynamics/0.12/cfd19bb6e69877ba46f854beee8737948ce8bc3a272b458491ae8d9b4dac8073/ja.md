```
exner(param_set, T, ρ[, q::PhasePartition)])
```

Exner関数は次のようになります。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `T` は温度です。
  * `ρ` は（湿った）空気の密度です。

オプションとして、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
