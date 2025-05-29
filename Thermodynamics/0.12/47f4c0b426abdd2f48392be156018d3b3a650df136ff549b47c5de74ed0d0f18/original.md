```
PhaseEquil_ρpq(param_set, ρ, p, q_tot[, perform_sat_adjust=true, maxiter, sat_adjust_method, T_guess])
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from temperature.

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `ρ` density
  * `p` pressure
  * `q_tot` total specific humidity
  * `perform_sat_adjust` Bool indicating to perform saturation adjustment
  * `maxiter` maximum number of iterations to perform in saturation adjustment
  * `sat_adjust_method` the numerical method to use.  See the [`Thermodynamics`](@ref) for options.
  * `T_guess` initial guess for temperature in saturation adjustment

TODO: change input argument order: perform*sat*adjust is       unique to this constructor, so it should be last.       (breaking change)
