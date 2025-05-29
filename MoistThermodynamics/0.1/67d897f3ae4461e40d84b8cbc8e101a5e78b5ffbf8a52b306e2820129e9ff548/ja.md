```
air_temperature_from_liquid_ice_pottemp_given_pressure(θ_liq_ice, p[, q::PhasePartition])
```

空気の温度は

  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `p` 圧力

そして、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気のものになります。
