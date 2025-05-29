```
FugDewPressure(kwargs...)
```

Method to compute [`dew_pressure`](@ref) via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the pressure. If no convergence is reached after `itmax_newton` iterations, the system is solved using a multidimensional non-linear system of equations.

Inputs:

  * `x0 = nothing`: optional, initial guess for the liquid phase composition
  * `p0 = nothing`: optional, initial guess for the dew pressure [`Pa`]
  * `vol0 = nothing`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton = 10`: optional, number of iterations to update the pressure using newton's method
  * `itmax_ss = 5`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x = 1e-8`: optional, tolerance to stop successive substitution cycle
  * `tol_p = 1e-8`: optional, tolerance to stop newton cycle
  * `tol_of = 1e-8`: optional, tolerance to check if the objective function is zero.
  * `noncondensables = nothing`: optional, Vector of strings containing non condensable compounds. those will be set to zero on the liquid phase.
