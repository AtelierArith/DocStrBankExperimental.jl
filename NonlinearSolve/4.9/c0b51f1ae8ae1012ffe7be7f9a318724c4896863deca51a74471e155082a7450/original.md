```
SIAMFANLEquationsJL(;
    method = :newton, delta = 1e-3, linsolve = nothing, autodiff = missing
)
```

### Keyword Arguments

  * `method`: the choice of method for solving the nonlinear system.
  * `delta`: initial pseudo time step, default is 1e-3.
  * `linsolve` : JFNK linear solvers, choices are `gmres` and `bicgstab`.
  * `m`: Depth for Anderson acceleration, default as 0 for Picard iteration.
  * `beta`: Anderson mixing parameter, change f(x) to (1-beta)x+beta*f(x), equivalent to accelerating damped Picard iteration.
  * `autodiff`: Defaults to `missing`, which means we will default to letting `SIAMFANLEquations` construct the jacobian if `f.jac` is not provided. In other cases, we use it to generate a jacobian similar to other NonlinearSolve solvers.

### Submethod Choice

  * `:newton`: Classical Newton method.
  * `:pseudotransient`: Pseudo transient method.
  * `:secant`: Secant method for scalar equations.
  * `:anderson`: Anderson acceleration for fixed point iterations.

!!! note
    This algorithm is only available if `SIAMFANLEquations.jl` is installed and loaded.

