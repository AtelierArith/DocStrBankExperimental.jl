```
SubGradientMethodState <: AbstractManoptSolverState
```

stores option values for a [`subgradient_method`](@ref) solver

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `p_star`: optimal value
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `X`: the current element from the possible subgradients at `p` that was last evaluated.

# Constructor

```
SubGradientMethodState(M::AbstractManifold; kwargs...)
```

Initialise the Subgradient method state

# Keyword arguments

  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stepsize=`[`default_stepsize`](@ref)`(M, SubGradientMethodState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector
