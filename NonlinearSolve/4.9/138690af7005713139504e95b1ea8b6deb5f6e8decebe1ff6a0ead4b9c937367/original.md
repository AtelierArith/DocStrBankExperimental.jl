```
NLSolversJL(method; autodiff = nothing)
NLSolversJL(; method, autodiff = nothing)
```

Wrapper over NLSolvers.jl Nonlinear Equation Solvers. We automatically construct the jacobian function and supply it to the solver.

### Arguments

  * `method`: the choice of method for solving the nonlinear system. See the documentation for NLSolvers.jl for more information.
  * `autodiff`: the choice of method for generating the Jacobian. Defaults to `nothing` which means that a default is selected according to the problem specification. Can be any valid ADTypes.jl autodiff type (conditional on that backend being supported in NonlinearSolve.jl).
