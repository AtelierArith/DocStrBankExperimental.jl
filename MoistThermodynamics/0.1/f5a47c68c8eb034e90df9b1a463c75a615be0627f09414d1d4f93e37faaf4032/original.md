```
air_temperature_from_liquid_ice_pottemp_non_linear(θ_liq_ice, ρ, q::PhasePartition)
```

Computes temperature `T` given

  * `θ_liq_ice` liquid-ice potential temperature
  * `ρ` (moist-)air density
  * `tol` tolerance for non-linear equation solve
  * `maxiter` maximum iterations for non-linear equation solve

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air,

by finding the root of $T - air_temperature_from_liquid_ice_pottemp_given_pressure(θ_liq_ice, air_pressure(T, ρ, q), q) = 0$
