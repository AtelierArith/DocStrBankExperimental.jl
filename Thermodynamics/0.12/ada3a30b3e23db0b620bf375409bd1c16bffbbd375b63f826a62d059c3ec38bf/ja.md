```
air_temperature(param_set, e_int, q::PhasePartition)
```

空気の温度は、次のように定義されます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `e_int` は単位質量あたりの内部エネルギーです。

そして、オプションとして、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
