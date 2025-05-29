```
exner(param_set, T, ρ[, q::PhasePartition)])
```

The Exner function where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
