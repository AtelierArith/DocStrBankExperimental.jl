```
FugBubbleTemperature(kwargs...)
```

Method to compute [`bubble_temperature`](@ref) via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the temperature. If no convergence is reached after `itmax_newton` iterations, the system is solved using a multidimensional non-linear system of equations.

Inputs:

  * `y = nothing`: optional, initial guess for the vapor phase composition.
  * `T0 = nothing`: optional, initial guess for the bubble temperature [`K`].
  * `vol0 = nothing`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton = 10`: optional, number of iterations to update the temperature using newton's method
  * `itmax_ss = 5`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x = 1e-8`: optional, tolerance to stop successive substitution cycle
  * `tol_T = 1e-8`: optional, tolerance to stop newton cycle
  * `tol_of = 1e-8`: optional, tolerance to check if the objective function is zero.
  * `nonvolatiles`: optional, Vector of strings containing non volatile compounds. those will be set to zero on the vapour phase.
