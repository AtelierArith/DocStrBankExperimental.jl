```
StochasticGradientDescentState <: AbstractGradientDescentSolverState
```

Store the following fields for a default stochastic gradient descent algorithm, see also [`ManifoldStochasticGradientObjective`](@ref) and [`stochastic_gradient_descent`](@ref).

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `direction`:  a direction update to use
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `evaluation_order`: specify whether to use a randomly permuted sequence (`:FixedRandom`:), a per cycle permuted sequence (`:Linear`) or the default, a `:Random` sequence.
  * `order`: stores the current permutation
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# Constructor

```
StochasticGradientDescentState(M::AbstractManifold; kwargs...)
```

Create a `StochasticGradientDescentState` with start point `p`.

# Keyword arguments

  * `direction=`[`StochasticGradientRule`](@ref)`(M, [`zero*vector`](@extref`ManifoldsBase.zero*vector-Tuple{AbstractManifold, Any}`)`(M, p)`)
  * `order_type=:RandomOrder``
  * `order=Int[]`: specify how to store the order of indices for the next epoche
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`default_stepsize`](@ref)`(M, StochasticGradientDescentState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector
