```
PhaseEquil_ρθq(param_set, ρ, θ_liq_ice, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from:

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `ρ` (moist-)air density
  * `θ_liq_ice` liquid-ice potential temperature
  * `q_tot` total specific humidity
  * `relative_temperature_tol` relative temperature tolerance for saturation adjustment
  * `maxiter` maximum iterations for saturation adjustment
  * `T_guess` initial guess for temperature in saturation adjustment
