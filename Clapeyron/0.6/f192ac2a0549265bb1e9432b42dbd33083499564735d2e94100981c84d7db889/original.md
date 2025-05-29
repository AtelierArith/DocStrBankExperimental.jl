```
dew_temperature_fug(model::EoSModel, p, y, x0, T0; vol0=(nothing,nothing),
                         itmax_newton = 10, itmax_ss = 5, tol_x = 1e-8,
                         tol_T = 1e-8, tol_of = 1e-8)
```

Function to compute dew temperature via fugacity coefficients. First it uses successive substitution to update the phase composition and a outer newtown loop to update the temperature. If no convergence is reached after itmax_newton iterations, the system is solved using a multidimensional non-linear system of equations.

Inputs: model: equation of state model

  * `P`: pressure [`Pa`]
  * `y`: vapor phase composition
  * `x0`: initial guess for the liquid phase composition
  * `T0`: initial guess for the dew temperature [`K`]
  * `vol0`: optional, initial guesses for the liquid and vapor phase volumes
  * `itmax_newton`: optional, number of iterations to update the temperature using newton's method
  * `itmax_ss`: optional, number of iterations to update the liquid phase composition using successive substitution
  * `tol_x`: optional, tolerance to stop successive substitution cycle
  * `tol_T`: optional, tolerance to stop newton cycle
  * `tol_of`: optional, tolerance to check if the objective function is zero.
  * `noncondensables`: optional, Vector of strings containing non condensable compounds. those will be set to zero on the liquid phase.

Returns: `T`: dew temperature `volx`: saturared liquid volume `voly`: saturared vapor volume `x`: saturated liquid composition
