```
GradientDescentState{P,T} <: AbstractGradientSolverState
```

Describes the state of a gradient based descent algorithm.

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `direction::`[`DirectionUpdateRule`](@ref) : a processor to handle the obtained gradient and compute a direction to “walk into”.
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# Constructor

```
GradientDescentState(M::AbstractManifold; kwargs...)
```

Initialize the gradient descent solver state, where

## Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$

## Keyword arguments

  * `direction=`[`IdentityUpdateRule`](@ref)`()`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(100)`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`default_stepsize`](@ref)`(M, GradientDescentState; retraction_method=retraction_method)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

# See also

[`gradient_descent`](@ref)
