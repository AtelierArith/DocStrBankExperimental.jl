```
ODESolver(solver, kwargs..)
```

ODE-solver options (`solver`, `tolerances`, etc.) used for solving the ODE model in a `PEtabODEProblem`.

Any `solver` from [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) and [Sundials.jl](https://github.com/SciML/Sundials.jl) is supported. For solver recommendations and default options used when an `ODESolver` is not provided when creating a `PEtabODEProblem`, see the documentation.

More information on the available options and solvers can also be found in the documentation for [DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/).

# Keyword Arguments

  * `abstol=1e-8`: Absolute tolerance when solving the ODE model. It is not recommended to   increase above 1e-6 for gradients in order to obtain accurate gradients.
  * `reltol=1e-8`: Absolute tolerance when solving the ODE model. It is not recommended to   increase above 1e-6 for gradients in order to obtain accurate gradients.
  * `dtmin=nothing`: Minimum acceptable step size when solving the ODE model.
  * `maxiters=10000`: Maximum number of iterations when solving the ODE model. Increasing   above the default value can cause parameter estimation to take substantial longer time.
  * `verbose::Bool=true`: Whether or not warnings are displayed if the solver exits early.   `true` is recommended to detect if a suboptimal choice of `solver`.
  * `adj_solver=solver`: Solver to use when solving the adjoint ODE. Only applicable if   `gradient_method=:Adjoint` when creating the `PEtabODEProblem`. Defaults to `solver`.
  * `abstol_adj=abstol`: Absolute tolerance when solving the adjoint ODE model. Only   applicable if `gradient_method=:Adjoint` when creating the `PEtabODEProblem`. Defaults   to `abstol`.
  * `reltol_adj=abstol`: Relative tolerance when solving the adjoint ODE model. Only   applicable if `gradient_method=:Adjoint` when creating the `PEtabODEProblem`. Defaults   to `reltol`.
