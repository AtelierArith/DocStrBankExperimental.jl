```
perlin_1d(; seed=nothing)
perlin_improved_1d(; seed=nothing)
```

Construct a sampler that outputs 1-dimensional Perlin "Improved" noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.

# Notes:

  * `perlin_improved_1d` is deprecated and will be removed in favor of `perlin_1d` in a future major version release.
  * It is *strongly* recommended not to use this function for quality noise; the results will be very regular. There are many tricks people have done to combat this issue, but they all have trade-offs that are not worth the burden.

    The recommended alternatives are to either use [`simplex_1d`](@ref simplex_1d), or use [`perlin_3d`](@ref perlin_3d) with 2 of the coordinates fixed, and not close to `0.0`, `0.5`, or `1.0`.
