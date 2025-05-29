```
air_temperature_from_liquid_ice_pottemp(θ_liq_ice, ρ, q::PhasePartition)
```

The temperature given

  * `θ_liq_ice` liquid-ice potential temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
