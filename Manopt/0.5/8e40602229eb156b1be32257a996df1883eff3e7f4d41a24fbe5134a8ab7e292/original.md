```
AlternatingGradientDescentState <: AbstractGradientDescentSolverState
```

Store the fields for an alternating gradient descent algorithm, see also [`alternating_gradient_descent`](@ref).

# Fields

  * `direction::`[`DirectionUpdateRule`](@ref)
  * `evaluation_order::Symbol`: whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle newly permuted sequence (`:Random`) or the default `:Linear` evaluation order.
  * `inner_iterations`: how many gradient steps to take in a component before alternating to the next
  * `order`: the current permutation
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `k`, ì`:              internal counters for the outer and inner iterations, respectively.

# Constructors

```
AlternatingGradientDescentState(M::AbstractManifold; kwargs...)
```

# Keyword arguments

  * `inner_iterations=5`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$
  * `order_type::Symbol=:Linear`
  * `order::Vector{<:Int}=Int[]`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`default_stepsize`](@ref)`(M, AlternatingGradientDescentState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$

Generate the options for point `p` and where `inner_iterations`, `order_type`, `order`, `retraction_method`, `stopping_criterion`, and `stepsize`` are keyword arguments
