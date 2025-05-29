```
PrimalDualSemismoothNewtonState <: AbstractPrimalDualSolverState
```

# Fields

  * `m::P`: a point on the manifold $\mathcal M$
  * `n::Q`: a point on the manifold $\mathcal N$
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `primal_stepsize::Float64`:  proximal parameter of the primal prox
  * `dual_stepsize::Float64`:    proximal parameter of the dual prox
  * `reg_param::Float64`:        regularisation parameter for the Newton matrix
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `update_primal_base`:        function to update the primal base
  * `update_dual_base`:          function to update the dual base
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

where for the update functions a [`AbstractManoptProblem`](@ref) `amp`, [`AbstractManoptSolverState`](@ref) `ams` and the current iterate `i` are the arguments. If you activate these to be different from the default identity, you have to provide `p.Λ` for the algorithm to work (which might be `missing`).

# Constructor

```
PrimalDualSemismoothNewtonState(M::AbstractManifold; kwargs...)
```

Generate a state for the [`primal_dual_semismooth_Newton`](@ref).

## Keyword arguments

  * `m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `n=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(N)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `primal_stepsize=1/sqrt(8)`
  * `dual_stepsize=1/sqrt(8)`
  * `reg_param=1e-5`
  * `update_primal_base=(amp, ams, k) -> o.m`
  * `update_dual_base=(amp, ams, k) -> o.n`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=``[`StopAfterIteration`](@ref)`(50)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
