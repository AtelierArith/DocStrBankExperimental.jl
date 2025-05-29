```
saturation_excess(param_set, T, ρ, phase_type, q::PhasePartition)
```

The saturation excess in equilibrium where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature
  * `ρ` (moist-)air density
  * `phase_type` a thermodynamic state type
  * `q` [`PhasePartition`](@ref)

The saturation excess is the difference between the total specific humidity `q.tot` and the saturation specific humidity in equilibrium, and it is defined to be nonzero only if this difference is positive.
