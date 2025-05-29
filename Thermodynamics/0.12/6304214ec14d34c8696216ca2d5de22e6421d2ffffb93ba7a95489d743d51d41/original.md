```
liquid_ice_pottemp_sat(param_set, T, ρ, phase_type[, q::PhasePartition, cpm])
```

The saturated liquid ice potential temperature where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature
  * `ρ` (moist-)air density
  * `phase_type` a thermodynamic state type

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
