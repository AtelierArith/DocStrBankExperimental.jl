```
GradientDescentState{P,T} <: AbstractGradientSolverState
```

Describes a Gradient based descent algorithm, with

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `p`:                  (`rand(M)` the current iterate
  * `X`:                  (`zero_vector(M,p)`) the current gradient $\operatorname{grad}f(p)$, initialised to zero vector.
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(100)`) a [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`default_stepsize`](@ref)`(M, GradientDescentState)`) a [`Stepsize`](@ref)
  * `direction`:          ([`IdentityUpdateRule`](@ref)) a processor to compute the gradient
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) the retraction to use, defaults to the default set for your manifold.

# Constructor

```
GradientDescentState(M, p=rand(M); X=zero_vector(M, p), kwargs...)
```

Generate gradient descent options, where `X` can be used to set the tangent vector to store the gradient in a certain type. All other fields are keyword arguments.

# See also

[`gradient_descent`](@ref)
