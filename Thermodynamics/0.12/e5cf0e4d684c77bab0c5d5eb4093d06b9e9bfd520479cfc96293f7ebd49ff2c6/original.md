```
specific_enthalpy(param_set, T[, q::PhasePartition])
```

The specific_enthalpy per unit mass, given a thermodynamic state `ts` or

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
