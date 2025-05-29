```
internal_energy(T[, q::PhasePartition])
```

単位質量あたりの内部エネルギーは、熱力学的状態 `ts` または

  * `T` 温度

および、オプションで

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
