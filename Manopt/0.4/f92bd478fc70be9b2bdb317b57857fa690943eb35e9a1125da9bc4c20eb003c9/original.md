```
ManifoldStochasticGradientObjective{T<:AbstractEvaluationType} <: AbstractManifoldGradientObjective{T}
```

A stochastic gradient objective consists of

  * a(n optional) cost function $f(p) = \displaystyle\sum_{i=1}^n f_i(p)$
  * an array of gradients, $\operatorname{grad}f_i(p), i=1,\ldots,n$ which can be given in two forms

      * as one single function $(\mathcal M, p) ↦ (X_1,…,X_n) ∈ (T_p\mathcal M)^n$
      * as a vector of functions $\bigl( (\mathcal M, p) ↦ X_1, …, (\mathcal M, p) ↦ X_n\bigr)$.

Where both variants can also be provided as [`InplaceEvaluation`](@ref) functions `(M, X, p) -> X`, where `X` is the vector of `X1,...,Xn` and `(M, X1, p) -> X1, ..., (M, Xn, p) -> Xn`, respectively.

# Constructors

```
ManifoldStochasticGradientObjective(
    grad_f::Function;
    cost=Missing(),
    evaluation=AllocatingEvaluation()
)
ManifoldStochasticGradientObjective(
    grad_f::AbstractVector{<:Function};
    cost=Missing(), evaluation=AllocatingEvaluation()
)
```

Create a Stochastic gradient problem with the gradient either as one function (returning an array of tangent vectors) or a vector of functions (each returning one tangent vector).

The optional cost can also be given as either a single function (returning a number) pr a vector of functions, each returning a value.

# Used with

[`stochastic_gradient_descent`](@ref)

Note that this can also be used with a [`gradient_descent`](@ref), since the (complete) gradient is just the sums of the single gradients.
