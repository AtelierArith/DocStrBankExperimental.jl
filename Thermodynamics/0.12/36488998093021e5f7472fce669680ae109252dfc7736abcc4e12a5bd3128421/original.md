```
virtual_temperature(param_set, T[, q::PhasePartition])
```

The virtual temperature where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
