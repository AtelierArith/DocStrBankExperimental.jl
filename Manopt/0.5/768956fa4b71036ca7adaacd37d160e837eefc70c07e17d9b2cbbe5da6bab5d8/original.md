```
ExactPenaltyMethodState{P,T} <: AbstractManoptSolverState
```

Describes the exact penalty method, with

# Fields

  * `ϵ`: the accuracy tolerance
  * `ϵ_min`: the lower bound for the accuracy tolerance
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `ρ`: the penalty parameter
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `u`: the smoothing parameter and threshold for violation of the constraints
  * `u_min`: the lower bound for the smoothing parameter and threshold for violation of the constraints
  * `θ_ϵ`: the scaling factor of the tolerance parameter
  * `θ_ρ`: the scaling factor of the penalty parameter
  * `θ_u`: the scaling factor of the smoothing parameter

# Constructor

```
ExactPenaltyMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
```

construct the exact penalty state.

```
ExactPenaltyMethodState(M::AbstractManifold, sub_problem;
    evaluation=AllocatingEvaluation(), kwargs...
```

)

construct the exact penalty state, where `sub_problem` is a closed form solution with `evaluation` as type of evaluation.

# Keyword arguments

  * `ϵ=1e-3`
  * `ϵ_min=1e-6`
  * `ϵ_exponent=1 / 100`: a shortcut for the scaling factor $θ_ϵ$
  * `θ_ϵ=(ϵ_min / ϵ)^(ϵ_exponent)`
  * `u=1e-1`
  * `u_min=1e-6`
  * `u_exponent=1 / 100`:  a shortcut for the scaling factor $θ_u$.
  * `θ_u=(u_min / u)^(u_exponent)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `ρ=1.0`
  * `θ_ρ=0.3`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`(`: a functor indicating that the stopping criterion is fulfilled [`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ_min)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-10) )`

# See also

[`exact_penalty_method`](@ref)
