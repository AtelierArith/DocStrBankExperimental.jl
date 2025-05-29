```
ConvexBundleMethodState <: AbstractManoptSolverState
```

Stores option values for a [`convex_bundle_method`](@ref) solver.

# Fields

THe following fields require a (real) number type `R`, as well as point type `P` and a tangent vector type `T``

  * `atol_λ::R`:                 tolerance parameter for the convex coefficients in λ
  * `atol_errors::R:             tolerance parameter for the linearization errors
  * `bundle<:AbstractVector{Tuple{<:P,<:T}}`: bundle that collects each iterate with the computed subgradient at the iterate
  * `bundle_cap::Int`: the maximal number of elements the bundle is allowed to remember
  * `diameter::R`: estimate for the diameter of the level set of the objective function at the starting point
  * `domain: the domain of``f``as a function`(M,p) -> b`that evaluates to true when the current candidate is in the domain of`f`, and false otherwise,
  * `g::T`:                      descent direction
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `k_max::R`:                  upper bound on the sectional curvature of the manifold
  * `linearization_errors<:AbstractVector{<:R}`: linearization errors at the last serious step
  * `m::R`:                      the parameter to test the decrease of the cost: $f(q_{k+1}) ≤ f(p_k) + m ξ$.
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `p_last_serious::P`:         last serious iterate
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `transported_subgradients`:  subgradients of the bundle that are transported to `p_last_serious`
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing a subgradient at the current iterate
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `ε::R`:                      convex combination of the linearization errors
  * `λ:::AbstractVector{<:R}`:   convex coefficients from the slution of the subproblem
  * `ξ`:                         the stopping parameter given by $ξ = -\lVert g\rvert^2 – ε$
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Constructor

```
ConvexBundleMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
ConvexBundleMethodState(M::AbstractManifold, sub_problem=convex_bundle_method_subsolver; evaluation=AllocatingEvaluation(), kwargs...)
```

Generate the state for the [`convex_bundle_method`](@ref) on the manifold `M`

## Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `sub_problem`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Keyword arguments

Most of the following keyword arguments set default values for the fields mentioned before.

  * `atol_λ=eps()`
  * `atol_errors=eps()`
  * `bundle_cap=25``
  * `m=1e-2`
  * `diameter=50.0`
  * `domain=(M, p) -> isfinite(f(M, p))`
  * `k_max=0`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConvexBundleMethodState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)` specify the type of tangent vector to use.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
