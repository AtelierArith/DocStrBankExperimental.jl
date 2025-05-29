```
internal_energy(param_set, T[, q::PhasePartition])
```

The internal energy per unit mass, given a thermodynamic state `ts` or

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
