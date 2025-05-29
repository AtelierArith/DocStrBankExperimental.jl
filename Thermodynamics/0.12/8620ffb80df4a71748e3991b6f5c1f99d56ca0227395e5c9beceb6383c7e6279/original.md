```
PhaseEquil_pθq(param_set, θ_liq_ice, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from:

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `p` air pressure
  * `θ_liq_ice` liquid-ice potential temperature
  * `q_tot` total specific humidity
  * `relative_temperature_tol` relative temperature tolerance for saturation adjustment
  * `maxiter` maximum iterations for saturation adjustment
  * `sat_adjust_method` the numerical method to use.
  * `T_guess` initial guess for temperature in saturation adjustment
