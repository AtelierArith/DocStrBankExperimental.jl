```
StopWhenGradientNormLess <: StoppingCriterion
```

A stopping criterion based on the current gradient norm.

# Fields

  * `norm`:      a function `(M::AbstractManifold, p, X) -> ℝ` that computes a norm of the gradient `X` in the tangent space at `p` on `M``
  * `threshold`: the threshold to indicate to stop when the distance is below this value

# Internal fields

  * `last_change` store the last change
  * `at_iteration` store the iteration at which the stop indication happened

# Constructor

```
StopWhenGradientNormLess(ε; norm=(M,p,X) -> norm(M,p,X))
```

Create a stopping criterion with threshold `ε` for the gradient, that is, this criterion indicates to stop when [`get_gradient`](@ref) returns a gradient vector of norm less than `ε`, where the norm to use can be specified in the `norm=` keyword.
