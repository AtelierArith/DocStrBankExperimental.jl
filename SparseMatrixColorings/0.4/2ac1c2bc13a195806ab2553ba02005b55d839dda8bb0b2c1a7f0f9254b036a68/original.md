```
DynamicDegreeBasedOrder{degtype,direction}(; reproduce_colpack=false)
```

Instance of [`AbstractOrder`](@ref) which sorts vertices using a dynamically computed degree.

This order works by assigning vertices to buckets based on their dynamic degree, and then updating buckets iteratively by transfering vertices between them.

# Type parameters

  * `degtype::Symbol`: can be `:forward` (for the forward degree) or `:back` (for the back degree)
  * `direction::Symbol`: can be `:low2high` (if the order is defined from lowest to highest, i.e. `1` to `n`) or `:high2low` (if the order is defined from highest to lowest, i.e. `n` to `1`)

# Concrete variants

  * [`IncidenceDegree`](@ref)
  * [`SmallestLast`](@ref)
  * [`DynamicLargestFirst`](@ref)

# Settings

  * `reproduce_colpack::Bool`: whether to manage the buckets in the exact same way as the original ColPack implementation.

      * When `reproduce_colpack=true`, we always append and remove vertices at the end of a bucket (unilateral).
      * When `reproduce_colpack=false` (the default), we can append and remove vertices either at the start or at the end of a bucket (bilateral).

Allowing modifications on both sides of a bucket enables storage optimization, with a single fixed-size vector for all buckets instead of one dynamically-sized vector per bucket. As a result, the default setting `reproduce_colpack=false` is slightly more memory-efficient.

# References

  * [*ColPack: Software for graph coloring and related problems in scientific computing*](https://dl.acm.org/doi/10.1145/2513109.2513110), Gebremedhin et al. (2013), Section 5
