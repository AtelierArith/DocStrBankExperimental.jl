```
AugmentedLagrangianMethodState{P,T} <: AbstractManoptSolverState
```

Describes the augmented Lagrangian method, with

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `ϵ`:     the accuracy tolerance
  * `ϵ_min`: the lower bound for the accuracy tolerance
  * `λ`:     the Lagrange multiplier with respect to the equality constraints
  * `λ_max`: an upper bound for the Lagrange multiplier belonging to the equality constraints
  * `λ_min`: a lower bound for the Lagrange multiplier belonging to the equality constraints
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `penalty`: evaluation of the current penalty term, initialized to `Inf`.
  * `μ`:     the Lagrange multiplier with respect to the inequality constraints
  * `μ_max`: an upper bound for the Lagrange multiplier belonging to the inequality constraints
  * `ρ`:     the penalty parameter
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `τ`:     factor for the improvement of the evaluation of the penalty parameter
  * `θ_ρ`:   the scaling factor of the penalty parameter
  * `θ_ϵ`:   the scaling factor of the accuracy tolerance
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled

# Constructor

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective,
    sub_problem, sub_state; kwargs...
)
```

construct an augmented Lagrangian method options, where the manifold `M` and the [`ConstrainedManifoldObjective`](@ref) `co` are used for manifold- or objective specific defaults.

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective,
    sub_problem; evaluation=AllocatingEvaluation(), kwargs...
)
```

construct an augmented Lagrangian method options, where the manifold `M` and the [`ConstrainedManifoldObjective`](@ref) `co` are used for manifold- or objective specific defaults, and `sub_problem` is a closed form solution with `evaluation` as type of evaluation.

## Keyword arguments

the following keyword arguments are available to initialise the corresponding fields

  * `ϵ=1e–3`
  * `ϵ_min=1e-6`
  * `λ=ones(n)`: `n` is the number of equality constraints in the [`ConstrainedManifoldObjective`](@ref) `co`.
  * `λ_max=20.0`
  * `λ_min=- λ_max`
  * `μ=ones(m)`: `m` is the number of inequality constraints in the [`ConstrainedManifoldObjective`](@ref) `co`.
  * `μ_max=20.0`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `ρ=1.0`
  * `τ=0.8`
  * `θ_ρ=0.3`
  * `θ_ϵ=(ϵ_min/ϵ)^(ϵ_exponent)`
  * stopping*criterion=[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)([`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ*min)`[` & `](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`[` | `](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`.

# See also

[`augmented_Lagrangian_method`](@ref)
