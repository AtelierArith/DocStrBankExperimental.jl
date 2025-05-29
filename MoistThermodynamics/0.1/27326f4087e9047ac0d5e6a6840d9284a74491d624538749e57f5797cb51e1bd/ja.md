```
virtual_pottemp(T, ρ[, q::PhasePartition])
```

仮想温度は次のように定義されます。

  * `T` 温度
  * `ρ` （湿った）空気の密度

そして、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
