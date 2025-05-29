```
SizeMax{K} <: AbstractProperty
SizeMax(k::Int)
```

The maximum-K set sizes. e.g. the largest size of the [`IndependentSet`](@ref)  problem is also know as the independence number.

  * The corresponding tensor element type are max-plus tropical number [`Tropical`](@ref) if `K` is `Single` and [`ExtendedTropical`](@ref) if `K` is an integer.
  * It is compatible with weighted Constraint Satisfaction Problems.
  * BLAS (on CPU) and GPU are supported only if `K` is `Single`,
