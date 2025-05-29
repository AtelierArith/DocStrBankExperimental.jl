```
air_density(param_set, T, p[, q::PhasePartition])
```

The (moist-)air density from the equation of state (ideal gas law) where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` air temperature
  * `p` pressure

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
