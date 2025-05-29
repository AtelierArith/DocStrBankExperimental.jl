```
total_energy(e_kin, e_pot, T[, q::PhasePartition])
```

単位質量あたりの総エネルギーは、次のように与えられます。

  * `e_kin` 単位質量あたりの運動エネルギー
  * `e_pot` 単位質量あたりの位置エネルギー
  * `T` 温度

そして、オプションとして、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
