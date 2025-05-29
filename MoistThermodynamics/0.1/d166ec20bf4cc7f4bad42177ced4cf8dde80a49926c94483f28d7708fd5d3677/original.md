```
PhasePartition_equil(T, ρ, q_tot)
```

Partition the phases in equilibrium, returning a [`PhasePartition`](@ref) object using the [`liquid_fraction`](@ref) function where

  * `T` temperature
  * `ρ` (moist-)air density
  * `q_tot` total specific humidity

The residual `q.tot - q.liq - q.ice` is the vapor specific humidity.
