```
PhaseEquil_phq(param_set, p, h, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from temperature.

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `p` pressure
  * `h` specific enthalpy
  * `q_tot` total specific humidity
  * `T_guess` initial guess for temperature in saturation adjustment
