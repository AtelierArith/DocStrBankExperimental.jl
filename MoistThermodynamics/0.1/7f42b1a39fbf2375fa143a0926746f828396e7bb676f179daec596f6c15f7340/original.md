```
air_density(T, p[, q::PhasePartition])
```

The (moist-)air density from the equation of state (ideal gas law) where

  * `T` air temperature
  * `p` pressure

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
