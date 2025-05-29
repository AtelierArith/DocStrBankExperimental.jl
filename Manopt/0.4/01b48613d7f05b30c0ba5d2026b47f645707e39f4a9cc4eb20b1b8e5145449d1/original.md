```
ExactPenaltyMethodState{P,T} <: AbstractManoptSolverState
```

Describes the exact penalty method, with

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `p`:                   a set point on a manifold as starting point
  * `sub_problem`:         an [`AbstractManoptProblem`](@ref) problem for the subsolver
  * `sub_state`:           an [`AbstractManoptSolverState`](@ref) for the subsolver
  * `ϵ`:                   (`1e–3`) the accuracy tolerance
  * `ϵ_min`:               (`1e-6`) the lower bound for the accuracy tolerance
  * `u`:                   (`1e–1`) the smoothing parameter and threshold for violation of the constraints
  * `u_min`:               (`1e-6`) the lower bound for the smoothing parameter and threshold for violation of the constraints
  * `ρ`:                   (`1.0`) the penalty parameter
  * `θ_ρ`:                 (`0.3`) the scaling factor of the penalty parameter
  * `stopping_criterion`:  ([`StopAfterIteration`](@ref)`(300) | (`[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min) &`[`StopWhenChangeLess`](@ref)`(min_stepsize))`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.

# Constructor

```
ExactPenaltyMethodState(M::AbstractManifold, p, sub_problem, sub_state; kwargs...)
```

construct an exact penalty options with the remaining previously mentioned fields as keywords using their provided defaults.

# See also

[`exact_penalty_method`](@ref)
