```
ManifoldGradientObjective{T<:AbstractEvaluationType} <: AbstractManifoldGradientObjective{T}
```

specify an objective containing a cost and its gradient

# Fields

  * `cost`:       a function $f: \mathcal M → ℝ$
  * `gradient!!`: the gradient $\operatorname{grad}f: \mathcal M → \mathcal T\mathcal M$ of the cost function $f$.

Depending on the [`AbstractEvaluationType`](@ref) `T` the gradient can have to forms

  * as a function `(M, p) -> X` that allocates memory for `X`, an [`AllocatingEvaluation`](@ref)
  * as a function `(M, X, p) -> X` that work in place of `X`, an [`InplaceEvaluation`](@ref)

# Constructors

```
ManifoldGradientObjective(cost, gradient; evaluation=AllocatingEvaluation())
```

# Used with

[`gradient_descent`](@ref), [`conjugate_gradient_descent`](@ref), [`quasi_Newton`](@ref)
