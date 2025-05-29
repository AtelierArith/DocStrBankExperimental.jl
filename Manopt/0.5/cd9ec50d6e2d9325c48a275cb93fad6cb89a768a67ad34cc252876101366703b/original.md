```
ProximalBundleMethodState <: AbstractManoptSolverState
```

stores option values for a [`proximal_bundle_method`](@ref) solver.

# Fields

  * `α`:                        curvature-dependent parameter used to update `η`
  * `α₀`:                       initialization value for `α`, used to update `η`
  * `approx_errors`:            approximation of the linearization errors at the last serious step
  * `bundle`:                   bundle that collects each iterate with the computed subgradient at the iterate
  * `bundle_size`:              the maximal size of the bundle
  * `c`:                        convex combination of the approximation errors
  * `d`:                        descent direction
  * `δ`:                        parameter for updating `μ`: if $δ < 0$ then $μ = \log(i + 1)$, else $μ += δ μ$
  * `ε`:                        stepsize-like parameter related to the injectivity radius of the manifold
  * `η`:                        curvature-dependent term for updating the approximation errors
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `λ`:                        convex coefficients that solve the subproblem
  * `m`:                        the parameter to test the decrease of the cost
  * `μ`:                        (initial) proximal parameter for the subproblem
  * `ν`:                        the stopping parameter given by $ν = - μ |d|^2 - c$
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `p_last_serious`:           last serious iterate
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `transported_subgradients`: subgradients of the bundle that are transported to `p_last_serious`
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing a subgradient at the current iterate
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Constructor

```
ProximalBundleMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
ProximalBundleMethodState(M::AbstractManifold, sub_problem=proximal_bundle_method_subsolver; evaluation=AllocatingEvaluation(), kwargs...)
```

Generate the state for the [`proximal_bundle_method`](@ref) on the manifold `M`

# Keyword arguments

  * `α₀=1.2`
  * `bundle_size=50`
  * `δ=1.0`
  * `ε=1e-2`
  * `μ=0.5`
  * `m=0.0125`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `sub_problem=`[`proximal_bundle_method_subsolver`](@ref)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`[`AllocatingEvaluation`](@ref):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)` specify the type of tangent vector to use.
