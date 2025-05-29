```
function dew_pressure_fug(model::EoSModel, T, y, x0, p0; vol0=(nothing,nothing),
                         itmax_newton = 10, itmax_ss = 5, tol_x = 1e-8,
                         tol_p = 1e-8, tol_of = 1e-8)
```

Function to compute dew pressure via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the pressure. If no convergence is reached after itmax_newton iterations, the system is solved using a multidimensional non-linear systems of equations.

Inputs:

  * `model`: equation of state model
  * `T`: dew temperature [`K`]
  * `y`: vapor phase composition
  * `x0`: initial guess for the liquid phase composition
  * `p0`: initial guess for the dew pressure [`Pa`]
  * `vol0`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton`: optional, number of iterations to update the pressure using newton's method
  * `itmax_ss`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x`: optional, tolerance to stop successive substitution cycle
  * `tol_p`: optional, tolerance to stop newton cycle
  * `tol_of`: optional, tolerance to check if the objective function is zero.
  * `noncondensables`: optional, Vector of strings containing non condensable compounds. those will be set to zero on the liquid phase.

Returns:

  * `p`: dew pressure
  * `volx`: saturared liquid volume
  * `voly`: saturared vapor volume
  * `x`: saturated liquid composition
