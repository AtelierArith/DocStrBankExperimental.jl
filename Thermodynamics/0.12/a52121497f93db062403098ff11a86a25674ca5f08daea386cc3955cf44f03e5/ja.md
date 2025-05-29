```
total_energy(param_set, e_kin, e_pot, T[, q::PhasePartition])
```

単位質量あたりの総エネルギーは、次のように与えられます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `e_kin` は単位質量あたりの運動エネルギー
  * `e_pot` は単位質量あたりの位置エネルギー
  * `T` は温度

そして、オプションとして、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。
