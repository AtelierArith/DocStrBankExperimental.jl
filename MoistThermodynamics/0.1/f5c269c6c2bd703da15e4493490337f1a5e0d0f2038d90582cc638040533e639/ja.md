```
air_temperature_from_liquid_ice_pottemp(θ_liq_ice, ρ, q::PhasePartition)
```

与えられた温度

  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `ρ` （湿った）空気の密度

および、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥した空気のものになります。
