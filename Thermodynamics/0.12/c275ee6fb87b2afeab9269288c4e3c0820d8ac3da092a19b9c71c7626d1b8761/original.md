```
PhaseEquil_ρeq(param_set, ρ, e_int, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

Moist thermodynamic phase, given

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `ρ` density
  * `e_int` internal energy
  * `q_tot` total specific humidity

and, optionally

  * `maxiter` maximum iterations for saturation adjustment
  * `relative_temperature_tol` relative temperature tolerance for saturation adjustment
  * `sat_adjust_method` the numerical method to use.  See the [`Thermodynamics`](@ref) for options.
  * `T_guess` initial guess for temperature in saturation adjustment
