```
liquid_ice_pottemp_given_pressure(T, p, q::PhasePartition)
```

液体-氷のポテンシャル温度は次のとおりです。

  * `T` 温度
  * `p` 圧力

および、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
