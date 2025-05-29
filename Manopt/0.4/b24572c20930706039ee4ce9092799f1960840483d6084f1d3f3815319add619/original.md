```
AlternatingGradientDescentState <: AbstractGradientDescentSolverState
```

Store the fields for an alternating gradient descent algorithm, see also [`alternating_gradient_descent`](@ref).

# Fields

  * `direction`:          (`AlternatingGradient(zero_vector(M, x))` a [`DirectionUpdateRule`](@ref)
  * `evaluation_order`:   (`:Linear`) whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle newly permuted sequence (`:Random`) or the default `:Linear` evaluation order.
  * `inner_iterations`:   (`5`) how many gradient steps to take in a component before alternating to the next
  * `order` the current permutation
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) a `retraction(M,x,ξ)` to use.
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(M)`) a [`Stepsize`](@ref)
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) a [`StoppingCriterion`](@ref)
  * `p`:                  the current iterate
  * `X`:                  (`zero_vector(M,p)`) the current gradient tangent vector
  * `k`, ì`:              internal counters for the outer and inner iterations, respectively.

# Constructors

```
AlternatingGradientDescentState(M, p; kwargs...)
```

Generate the options for point `p` and where `inner_iterations`, `order_type`, `order`, `retraction_method`, `stopping_criterion`, and `stepsize`` are keyword arguments
