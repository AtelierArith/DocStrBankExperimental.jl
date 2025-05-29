```
QuasiNewtonAlgorithm(;
    linesearch = missing, trustregion = missing, descent, update_rule, reinit_rule,
    initialization, max_resets::Int = typemax(Int), name::Symbol = :unknown,
    max_shrink_times::Int = typemax(Int), concrete_jac = Val(false)
)
```

Nonlinear Solve Algorithms using an Iterative Approximation of the Jacobian. Most common examples include [`Broyden`](@ref)'s Method.

### Keyword Arguments

  * `trustregion`: Globalization using a Trust Region Method. This needs to follow the [`NonlinearSolveBase.AbstractTrustRegionMethod`](@ref) interface.
  * `descent`: The descent method to use to compute the step. This needs to follow the [`NonlinearSolveBase.AbstractDescentDirection`](@ref) interface.
  * `max_shrink_times`: The maximum number of times the trust region radius can be shrunk before the algorithm terminates.
  * `update_rule`: The update rule to use to update the Jacobian. This needs to follow the [`NonlinearSolveBase.AbstractApproximateJacobianUpdateRule`](@ref) interface.
  * `reinit_rule`: The reinitialization rule to use to reinitialize the Jacobian. This needs to follow the [`NonlinearSolveBase.AbstractResetCondition`](@ref) interface.
  * `initialization`: The initialization method to use to initialize the Jacobian. This needs to follow the [`NonlinearSolveBase.AbstractJacobianInitialization`](@ref) interface.
