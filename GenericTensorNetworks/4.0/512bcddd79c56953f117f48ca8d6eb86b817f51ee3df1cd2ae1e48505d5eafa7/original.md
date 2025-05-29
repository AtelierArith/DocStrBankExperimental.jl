```
CountingMin{K} <: AbstractProperty
CountingMin(K=Single)
```

Counting the number of sets with smallest-K size.

  * The corresponding tensor element type is inverted [`CountingTropical`](@ref) if `K` is `Single`, and [`TruncatedPoly`](@ref)`{K}` if `K` is an integer.
  * Weighted constraint satisfaction problems is only supported if `K` is `Single`.
  * GPU is supported,
