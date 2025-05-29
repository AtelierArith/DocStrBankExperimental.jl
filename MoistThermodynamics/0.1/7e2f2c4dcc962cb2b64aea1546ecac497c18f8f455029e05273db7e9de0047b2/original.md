```
liquid_ice_pottemp(T, ρ, q::PhasePartition)
```

The liquid-ice potential temperature where

  * `T` temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
