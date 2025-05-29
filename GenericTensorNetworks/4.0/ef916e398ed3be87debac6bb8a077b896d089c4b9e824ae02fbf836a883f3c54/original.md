```
CountingMax{K} <: AbstractProperty
CountingMax(K=Single)
```

Counting the number of sets with largest-K size. e.g. for [`IndependentSet`](@ref) problem, it counts independent sets of size $\alpha(G), \alpha(G)-1, \ldots, \alpha(G)-K+1$.

  * The corresponding tensor element type is [`CountingTropical`](@ref) if `K` is `Single`, and [`TruncatedPoly`](@ref)`{K}` if `K` is an integer.
  * Weighted constraint satisfaction problems is only supported if `K` is `Single`.
  * GPU is supported,
