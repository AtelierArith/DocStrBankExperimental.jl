```
soundspeed_air(param_set, T[, q::PhasePartition])
```

The speed of sound in unstratified air, where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
