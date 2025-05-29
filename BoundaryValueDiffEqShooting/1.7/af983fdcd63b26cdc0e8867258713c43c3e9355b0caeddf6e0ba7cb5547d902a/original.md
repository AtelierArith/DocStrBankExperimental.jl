```
Shooting(ode_alg; kwargs...)
Shooting(ode_alg, nlsolve; kwargs...)
Shooting(; ode_alg = nothing, nlsolve = nothing, jac_alg = nothing)
```

Single shooting method, reduces BVP to an initial value problem and solves the IVP.

## Arguments

  * `ode_alg`: ODE algorithm to use for solving the IVP. Any solver which conforms to the SciML `ODEProblem` interface can be used! (Defaults to `nothing` which will use poly-algorithm if `DifferentialEquations.jl` is loaded else this must be supplied)
  * `nlsolve`: Internal Nonlinear solver. Any solver which conforms to the SciML `NonlinearProblem` interface can be used. Note that any autodiff argument for the solver will be ignored and a custom jacobian algorithm will be used.
  * `jac_alg`: Jacobian Algorithm used for the Nonlinear Solver. If this is not set, we check if `nlsolve.ad` exists and is not nothing. If it is, we use that to construct the jacobian. If not, we try to use the best algorithm based on the input types and problem type. If `BVPJacobianAlgorithm` is provided, only `diffmode` is used (defaults to `AutoForwardDiff` if possible else `AutoFiniteDiff`).
