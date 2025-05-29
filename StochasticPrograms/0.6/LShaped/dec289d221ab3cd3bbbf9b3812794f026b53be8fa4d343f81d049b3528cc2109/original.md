```
RegularizedDecomposition
```

Functor object for using regularized decomposition regularization in an L-shaped algorithm. Create by supplying an [`RD`](@ref) object through `regularize` in `LShaped.Optimizer` or by setting the [`Regularizer`](@ref) attribute.

...

# Parameters

  * `σ::AbstractFloat = 1.0`: Initial value of regularization parameter. Controls the relative penalty of the deviation from the current major iterate.
  * `σ̅::AbstractFloat = 4.0`: Maximum value of the regularization parameter.
  * `σ̲::AbstractFloat = 0.5`: Minimum value of the regularization parameter.
  * `log::Bool = true`: Specifices if L-shaped procedure should be logged on standard output or not.
  * `penaltyterm::PenaltyTerm = Quadratic`: Specify penaltyterm variant ([`Quadratic`](@ref), [`InfNorm`](@ref), [`ManhattanNorm`][@ref])

...
