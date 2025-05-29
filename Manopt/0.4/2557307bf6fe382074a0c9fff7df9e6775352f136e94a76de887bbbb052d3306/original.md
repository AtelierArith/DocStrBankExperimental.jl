```
ConjugateGradientState <: AbstractGradientSolverState
```

specify options for a conjugate gradient descent algorithm, that solves a [`DefaultManoptProblem`].

# Fields

  * `p`:                       the current iterate, a point on a manifold
  * `X`:                       the current gradient, also denoted as $ξ$ or $X_k$ for the gradient in the $k$th step.
  * `δ`:                       the current descent direction, also a tangent vector
  * `β`:                       the current update coefficient rule, see .
  * `coefficient`:             ([`ConjugateDescentCoefficient`](@ref)`()`) a [`DirectionUpdateRule`](@ref) function to determine the new `β`
  * `stepsize`:                ([`default_stepsize`](@ref)`(M, ConjugateGradientDescentState; retraction_method=retraction_method)`) a [`Stepsize`](@ref) function
  * `stop`:                    ([`StopAfterIteration`](@ref)`(500) |`[`StopWhenGradientNormLess`](@ref)`(1e-8)`) a [`StoppingCriterion`](@ref)
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) a type of retraction
  * `vector_transport_method`: (`default_retraction_method(M, typeof(p))`) a type of retraction

# Constructor

```
ConjugateGradientState(M, p)
```

where the last five fields can be set by their names as keyword and the `X` can be set to a tangent vector type using the keyword `initial_gradient` which defaults to `zero_vector(M,p)`, and `δ` is initialized to a copy of this vector.

# See also

[`conjugate_gradient_descent`](@ref), [`DefaultManoptProblem`](@ref), [`ArmijoLinesearch`](@ref)
