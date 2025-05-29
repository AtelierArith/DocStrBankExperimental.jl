```
GeneralizedFirstOrderAlgorithm(;
    descent, linesearch = missing,
    trustregion = missing, autodiff = nothing, vjp_autodiff = nothing,
    jvp_autodiff = nothing, max_shrink_times::Int = typemax(Int),
    concrete_jac = Val(false), name::Symbol = :unknown
)
```

This is a Generalization of First-Order (uses Jacobian) Nonlinear Solve Algorithms. The most common example of this is Newton-Raphson Method.

First Order here refers to the order of differentiation, and should not be confused with the order of convergence.

### Keyword Arguments

  * `trustregion`: Globalization using a Trust Region Method. This needs to follow the [`NonlinearSolveBase.AbstractTrustRegionMethod`](@ref) interface.
  * `descent`: The descent method to use to compute the step. This needs to follow the [`NonlinearSolveBase.AbstractDescentDirection`](@ref) interface.
  * `max_shrink_times`: The maximum number of times the trust region radius can be shrunk before the algorithm terminates.
