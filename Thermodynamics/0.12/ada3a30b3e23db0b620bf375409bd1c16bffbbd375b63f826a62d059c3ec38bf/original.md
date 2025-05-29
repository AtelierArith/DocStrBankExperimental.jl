```
air_temperature(param_set, e_int, q::PhasePartition)
```

The air temperature, where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `e_int` internal energy per unit mass

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
