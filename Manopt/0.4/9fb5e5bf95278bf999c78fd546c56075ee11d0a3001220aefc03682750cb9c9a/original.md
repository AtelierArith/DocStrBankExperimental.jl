```
StochasticGradientDescentState <: AbstractGradientDescentSolverState
```

Store the following fields for a default stochastic gradient descent algorithm, see also [`ManifoldStochasticGradientObjective`](@ref) and [`stochastic_gradient_descent`](@ref).

# Fields

  * `p`:                  the current iterate
  * `direction`:          ([`StochasticGradient`](@ref)) a direction update to use
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) a [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(1.0)`) a [`Stepsize`](@ref)
  * `evaluation_order`:   (`:Random`) specify whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle permuted sequence (`:Linear`) or the default `:Random` one.
  * `order`:              the current permutation
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) a `retraction(M, p, X)` to use.

# Constructor

```
StochasticGradientDescentState(M, p)
```

Create a `StochasticGradientDescentState` with start point `p`. all other fields are optional keyword arguments, and the defaults are taken from `M`.
