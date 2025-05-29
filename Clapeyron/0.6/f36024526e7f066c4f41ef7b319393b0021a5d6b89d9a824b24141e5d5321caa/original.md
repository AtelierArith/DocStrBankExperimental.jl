```
bubble_temperature_fug(model::EoSModel, p, x, y0, T0; vol0=(nothing,nothing),
                     itmax_newton = 10, itmax_ss = 5, tol_y = 1e-8,
                     tol_T = 1e-8, tol_of = 1e-8)
```

Function to compute bubble temperature via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the temperature. If no convergence is reached after itmax_newton iterations, the system is solved using a multidimensional non-linear systems of equations.

Inputs:

  * model: equation of state model
  * `P`: pressure [`Pa`]
  * `x`: liquid phase composition
  * `y`: initial guess for the vapor phase composition
  * `T0`: initial guess for the bubble temperature [`K`]
  * `vol0`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton`: optional, number of iterations to update the temperature using newton's method
  * `itmax_ss`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x`: optional, tolerance to stop successive substitution cycle
  * `tol_T`: optional, tolerance to stop newton cycle
  * `tol_of`: optional, tolerance to check if the objective function is zero.
  * `nonvolatiles`: optional, Vector of strings containing non volatile compounds. those will be set to zero on the vapour phase.

Returns:

  * `T`: bubble temperature
  * `volx`: saturared liquid volume
  * `voly`: saturared vapor volume
  * `y`: saturated vapor composition
