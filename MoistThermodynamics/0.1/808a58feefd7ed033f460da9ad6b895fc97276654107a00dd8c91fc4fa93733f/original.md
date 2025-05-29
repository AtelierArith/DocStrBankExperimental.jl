```
air_pressure(T, ρ[, q::PhasePartition])
```

The air pressure from the equation of state (ideal gas law) where

  * `T` air temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
