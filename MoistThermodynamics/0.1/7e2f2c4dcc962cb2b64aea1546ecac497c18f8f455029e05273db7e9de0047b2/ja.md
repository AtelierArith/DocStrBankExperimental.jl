```
liquid_ice_pottemp(T, ρ, q::PhasePartition)
```

液体-氷の潜在温度は次のように定義されます。

  * `T` 温度
  * `ρ` （湿った）空気の密度

および、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
