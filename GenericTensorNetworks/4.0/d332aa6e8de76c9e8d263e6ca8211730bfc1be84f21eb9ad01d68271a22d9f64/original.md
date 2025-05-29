```
SizeMin{K} <: AbstractProperty
SizeMin(k::Int)
```

The minimum-K set sizes. e.g. the smallest size ofthe [`MaximalIS`](@ref) problem is also known as the independent domination number.

  * The corresponding tensor element type are inverted max-plus tropical number [`Tropical`](@ref) if `K` is `Single` and inverted [`ExtendedTropical`](@ref) `K` is an integer.

The inverted Tropical number emulates the min-plus tropical number.

  * It is compatible with weighted constraint satisfaction problems.
  * BLAS (on CPU) and GPU are supported only if `K` is `Single`,
