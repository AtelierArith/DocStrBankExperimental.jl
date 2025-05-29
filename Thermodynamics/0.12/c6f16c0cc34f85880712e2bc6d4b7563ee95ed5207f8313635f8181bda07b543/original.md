```
PhaseNonEquil_ρθq(param_set, ρ, θ_liq_ice, q_pt)
```

Constructs a [`PhaseNonEquil`](@ref) thermodynamic state from:

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `ρ` (moist-)air density
  * `θ_liq_ice` liquid-ice potential temperature
  * `q_pt` phase partition

and, optionally

  * `relative_temperature_tol` potential temperature for non-linear equation solve
  * `maxiter` maximum iterations for non-linear equation solve
