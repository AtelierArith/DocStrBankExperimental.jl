```
ManifoldCostGradientObjective{T} <: AbstractManifoldObjective{T}
```

specify an objective containing one function to perform a combined computation of cost and its gradient

# Fields

  * `costgrad!!`: a function that computes both the cost $f: \mathcal M → ℝ$ and its gradient $\operatorname{grad}f: \mathcal M → \mathcal T\mathcal M$

Depending on the [`AbstractEvaluationType`](@ref) `T` the gradient can have to forms

  * as a function `(M, p) -> (c, X)` that allocates memory for the gradient `X`, an [`AllocatingEvaluation`](@ref)
  * as a function `(M, X, p) -> (c, X)` that work in place of `X`, an [`InplaceEvaluation`](@ref)

# Constructors

```
ManifoldCostGradientObjective(costgrad; evaluation=AllocatingEvaluation())
```

# Used with

[`gradient_descent`](@ref), [`conjugate_gradient_descent`](@ref), [`quasi_Newton`](@ref)
