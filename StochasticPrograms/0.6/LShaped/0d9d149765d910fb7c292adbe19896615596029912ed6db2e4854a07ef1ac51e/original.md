```
LevelSet
```

Functor object for using level-set regularization in an L-shaped algorithm. Create by supplying an [`LV`](@ref) object through `regularize` in `LShaped.Optimizer` or by setting the [`Regularizer`](@ref) attribute.

...

# Parameters

  * `λ::AbstractFloat = 0.5`: Controls the level position L = (1-λ)*θ + λ*Q̃, a convex combination of the current lower and upper bound.
  * `penaltyterm::PenaltyTerm = Quadratic`: Specify penaltyterm variant ([`Quadratic`](@ref), [`InfNorm`](@ref), [`ManhattanNorm`][@ref])

...
