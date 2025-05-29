```
GeneralizedXYFlash{T}(;kwargs...)
```

Method to solve non-reactive multicomponent, two-phase flash problem, using a generalized formulation.

Only two phases are supported. if `K0` is `nothing`, it will be calculated via fugacity coefficients at p,T conditions.

### Keyword Arguments:

  * `equilibrium` (optional) = equilibrium type ":vle" for liquid vapor equilibria, ":lle" for liquid liquid equilibria, `:unknown` if not specified
  * `p0` (optional), initial guess pressure, ignored if pressure is one of the flash specifications.
  * `T0` (optional), initial guess temperature, ignored if temperature is one of the flash specifications.
  * `K0` (optional), initial guess for the constants K
  * `x0` (optional), initial guess for the composition of phase x
  * `y0` = optional, initial guess for the composition of phase y
  * `vol0` = optional, initial guesses for phase x and phase y volumes
  * `atol` = absolute tolerance to stop the calculation
  * `rtol` = relative tolerance to stop the calculation
  * `max_iters` = maximum number of iterations
