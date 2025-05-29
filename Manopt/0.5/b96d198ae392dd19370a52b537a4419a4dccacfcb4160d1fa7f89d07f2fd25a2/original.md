```
ProjectedGradientMethodState <: AbstractManoptSolverState
```

# Fields

  * `backtracking::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size to determine the step size $β_k$ step size from $p_k$ to the candidate $q_k$
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `q` an interims point for the projected gradient step
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size $α_k$ to determine the $q_k$ candidate
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `Y::T` a temporary memory for a tangent vector to store the no. Used within the backtracking

# Constructor

```
ProjectedGradientMethodState(M, p=rand(M); kwargs...)
```

## Keyword arguments

  * `backtracking=`[`ArmijoLinesearchStepsize`](@ref)`(M)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size $p_k$ to the candidate $q_k$
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`ConstantStepsize`](@ref)`(M)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size $α_k$ to determine the $q_k$ candidate
  * `stop=`[`StopAfterIteration`](@ref)`(300)`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
