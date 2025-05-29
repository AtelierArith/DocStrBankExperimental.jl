```
bubble_pressure_fug(model::EoSModel, T, x, y0, p0; vol0=(nothing,nothing),
                     itmax_newton = 10, itmax_ss = 5, tol_y = 1e-8,
                     tol_p = 1e-8, tol_of = 1e-8)
```

Function to compute bubble pressure via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the pressure. If no convergence is reached after itmax_newton iterations, the system is solved using a multidimensional non-linear systems of equations.

Inputs: model: equation of state model

  * `T`: bubble temperature [`K`]
  * `x`: liquid phase composition
  * `y0`: initial guess for the vapor phase composition
  * `p0`: initial guess for the bubble pressure [`Pa`]
  * `vol0`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton`: optional, number of iterations to update the pressure using newton's method
  * `itmax_ss`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x`: optional, tolerance to stop successive substitution cycle
  * `tol_p`: optional, tolerance to stop newton cycle
  * `tol_of`: optional, tolerance to check if the objective function is zero.
  * `nonvolatiles = nothing`: optional, Vector of strings containing non volatile compounds. those will be set to zero on the vapour phase.

Returns: `p`: bubble pressure `volx`: saturared liquid volume `voly`: saturared vapor volume `y`: saturated vapor composition
