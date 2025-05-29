```
ActivityDewTemperature(kwargs...)
```

Function to compute [`dew_temperature`](@ref) using Activity Coefficients. On activity coefficient models it solves the problem via succesive substitucion. On helmholtz-based models, it uses the Chapman approximation for activity coefficients.

Inputs:

  * `gas_fug = true`: if the solver uses gas fugacity coefficients. on `ActivityModel` is set by default to `false`
  * `poynting = true`: if the solver use the poynting correction on the liquid fugacity coefficients. on `ActivityModel` is set by default to `false`
  * `x0 = nothing`: optional, initial guess for the liquid phase composition
  * `T0 = nothing`: optional, initial guess for the dew temperature [`K`]
  * `vol0 = nothing`: optional, initial guesses for the liquid and vapor phase volumes
  * `atol = 1e-8`: optional, absolute tolerance of the non linear system of equations
  * `rtol = 1e-12`: optional, relative tolerance of the non linear system of equations
  * `itmax_ss = 40`: optional, maximum number of sucesive substitution iterations
