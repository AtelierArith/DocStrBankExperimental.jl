```
AugmentedLagrangianMethodState{P,T} <: AbstractManoptSolverState
```

Describes the augmented Lagrangian method, with

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `p`:                  a point on a manifold as starting point and current iterate
  * `sub_problem`:        an [`AbstractManoptProblem`](@ref) problem for the subsolver
  * `sub_state`:          an [`AbstractManoptSolverState`](@ref) for the subsolver
  * `ϵ`:                  (`1e–3`) the accuracy tolerance
  * `ϵ_min`:              (`1e-6`) the lower bound for the accuracy tolerance
  * `λ`:                  (`ones(n)`) the Lagrange multiplier with respect to the equality constraints
  * `λ_max`:              (`20.0`) an upper bound for the Lagrange multiplier belonging to the equality constraints
  * `λ_min`:              (`- λ_max`) a lower bound for the Lagrange multiplier belonging to the equality constraints
  * `μ`:                  (`ones(m)`) the Lagrange multiplier with respect to the inequality constraints
  * `μ_max`:              (`20.0`) an upper bound for the Lagrange multiplier belonging to the inequality constraints
  * `ρ`:                  (`1.0`) the penalty parameter
  * `τ`:                  (`0.8`) factor for the improvement of the evaluation of the penalty parameter
  * `θ_ρ`:                (`0.3`) the scaling factor of the penalty parameter
  * `θ_ϵ`:                ((`(ϵ_min/ϵ)^(ϵ_exponent)`) the scaling factor of the accuracy tolerance
  * `penalty`:            evaluation of the current penalty term, initialized to `Inf`.
  * `stop`: (`(`[`StopAfterIteration`](@ref)`(300) | (`[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min) &`[`StopWhenChangeLess`](@ref)`(1e-10))`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.

# Constructor

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective, p; kwargs...)
```

construct an augmented Lagrangian method options with the fields and defaults as stated before, where the manifold `M` and the [`ConstrainedManifoldObjective`](@ref) `co` can be helpful for manifold- or objective specific defaults.

# See also

[`augmented_Lagrangian_method`](@ref)
