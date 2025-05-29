```
TrustRegionsState <: AbstractHessianSolverState
```

Store the state of the trust-regions solver.

# Fields

  * `acceptance_rate`:         a lower bound of the performance ratio for the iterate that decides if the iteration is accepted or not.
  * `HX`, `HY`, `HZ`:          interim storage (to avoid allocation) of ``\operatorname{Hess} f(p)[⋅]` of `X`, `Y`, `Z`
  * `max_trust_region_radius`: the maximum trust-region radius
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `project!`:                for numerical stability it is possible to project onto the tangent space after every iteration. the function has to work inplace of `Y`, that is `(M, Y, p, X) -> Y`, where `X` and `Y` can be the same memory.
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `randomize`:               indicate whether `X` is initialised to a random vector or not
  * `ρ_regularization`:        regularize the model fitness $ρ$ to avoid division by zero
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `σ`:                       Gaussian standard deviation when creating the random initial tangent vector This field has no effect, when `randomize` is false.
  * `trust_region_radius`: the trust-region radius
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `Y`:                       the solution (tangent vector) of the subsolver
  * `Z`:                       the Cauchy point (only used if random is activated)

# Constructors

```
TrustRegionsState(M, mho::AbstractManifoldHessianObjective; kwargs...)
TrustRegionsState(M, sub_problem, sub_state; kwargs...)
TrustRegionsState(M, sub_problem; evaluation=AllocatingEvaluation(), kwargs...)
```

create a trust region state.

  * given a [`AbstractManifoldHessianObjective`](@ref) `mho`, the default sub solver, a [`TruncatedConjugateGradientState`](@ref) with `mho` used to define the problem on a tangent space is created
  * given a `sub_problem` and an `evaluation=` keyword, the sub problem solver is assumed to be the closed form solution, where `evaluation` determines how to call the sub function.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `sub_problem`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

## Keyword arguments

  * `acceptance_rate=0.1`
  * `max_trust_region_radius=sqrt(manifold_dimension(M))`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `project!=copyto!`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: a functor indicating that the stopping criterion is fulfilled
  * `randomize=false`
  * `ρ_regularization=10000.0`
  * `θ=1.0`
  * `trust_region_radius=max_trust_region_radius / 8`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

# See also

[`trust_regions`](@ref)
