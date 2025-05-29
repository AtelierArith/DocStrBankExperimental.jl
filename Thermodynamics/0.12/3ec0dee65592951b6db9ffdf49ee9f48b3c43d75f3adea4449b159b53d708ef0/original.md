```
PhasePartition_equil(param_set, T, ρ, q_tot, phase_type)
PhasePartition_equil(param_set, T, ρ, q_tot, p_vap_sat, λ)
```

Partition the phases in equilibrium, returning a [`PhasePartition`](@ref) object using the [`liquid_fraction`](@ref) function where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `T` temperature
  * `ρ` (moist-)air density
  * `q_tot` total specific humidity
  * `phase_type` a thermodynamic state type
  * `p_vap_sat` saturation vapor pressure
  * `λ` liquid fraction

The residual `q.tot - q.liq - q.ice` is the vapor specific humidity.
