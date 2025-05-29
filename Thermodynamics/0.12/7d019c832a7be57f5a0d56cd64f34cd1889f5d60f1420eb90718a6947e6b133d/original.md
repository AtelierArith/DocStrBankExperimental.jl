```
air_pressure(param_set, T, ρ[, q::PhasePartition])
```

The air pressure from the equation of state (ideal gas law) where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` air temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
