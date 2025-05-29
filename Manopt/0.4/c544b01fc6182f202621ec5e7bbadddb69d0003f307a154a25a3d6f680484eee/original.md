```
TrustRegionsState <: AbstractHessianSolverState
```

Store the state of the trust-regions solver.

# Fields

All the following fields (besides `p`) can be set by specifying them as keywords.

  * `acceptance_rate`:         (`0.1`) a lower bound of the performance ratio for the iterate that decides if the iteration is accepted or not.
  * `max_trust_region_radius`: (`sqrt(manifold_dimension(M))`) the maximum trust-region radius
  * `p`:                       (`rand(M)` if a manifold is provided) the current iterate
  * `project!`:                (`copyto!`) specify a projection operation for tangent vectors for numerical stability. A function `(M, Y, p, X) -> ...` working in place of `Y`. per default, no projection is performed, set it to `project!` to activate projection.
  * `stop`:                    ([`StopAfterIteration`](@ref)`(1000) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`)
  * `randomize`:               (`false`) indicates if the trust-region solve is to be initiated with a random tangent vector. If set to true, no preconditioner is used. This option is set to true in some scenarios to escape saddle points, but is otherwise seldom activated.
  * `ρ_regularization`:        (`10000.0`) regularize the model fitness $ρ$ to avoid division by zero
  * `sub_problem`:             an [`AbstractManoptProblem`](@ref) problem or a function `(M, p, X) -> q` or `(M, q, p, X)` for the a closed form solution of the sub problem
  * `sub_state`:               ([`TruncatedConjugateGradientState`](@ref)`(M, p, X)`)
  * `σ`:                       (`0.0` or `1e-6` depending on `randomize`) Gaussian standard deviation when creating the random initial tangent vector
  * `trust_region_radius`:     (`max_trust_region_radius / 8`) the (initial) trust-region radius
  * `X`:                       (`zero_vector(M,p)`) the current gradient `grad_f(p)` Use this default to specify the type of tangent vector to allocate also for the internal (tangent vector) fields.

# Internal fields

  * `HX`, `HY`, `HZ`:          interim storage (to avoid allocation) of ``\operatorname{Hess} f(p)[\cdot]` of `X`, `Y`, `Z`
  * `Y`:                       the solution (tangent vector) of the subsolver
  * `Z`:                       the Cauchy point (only used if random is activated)

# Constructors

All the following constructors have the fields as keyword arguments with the defaults given in brackets. If no initial point `p` is provided, `p=rand(M)` is used

```
TrustRegionsState(M, mho; kwargs...)
TrustRegionsState(M, p, mho; kwargs...)
```

A trust region state, where the sub problem is set to a [`DefaultManoptProblem`](@ref) on the tangent space using the [`TrustRegionModelObjective`](@ref) to be solved with [`truncated_conjugate_gradient_descent!`](@ref) or in other words the sub state is set to [`TruncatedConjugateGradientState`](@ref).

```
TrustRegionsState(M, sub_problem, sub_state; kwargs...)
TrustRegionsState(M, p, sub_problem, sub_state; kwargs...)
```

A trust region state, where the sub problem is solved using a [`AbstractManoptProblem`](@ref) `sub_problem` and an [`AbstractManoptSolverState`](@ref) `sub_state`.

```
TrustRegionsState(M, f::Function; evaluation=AllocatingEvaluation, kwargs...)
TrustRegionsState(M, p, f; evaluation=AllocatingEvaluation, kwargs...)
```

A trust region state, where the sub problem is solved in closed form by a function `f(M, p, Y, Δ)`, where `p` is the current iterate, `Y` the initial tangent vector at `p` and `Δ` the current trust region radius.

# See also

[`trust_regions`](@ref), [`trust_regions!`](@ref)
