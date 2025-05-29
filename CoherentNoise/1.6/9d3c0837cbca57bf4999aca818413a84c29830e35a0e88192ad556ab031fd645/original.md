```
perlin_3d(; seed=nothing)
perlin_improved_3d(; seed=nothing)
```

Construct a sampler that outputs 3-dimensional Perlin "Improved" noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.

# Notes:

  * `perlin_improved_3d` is deprecated and will be removed in favor of `perlin_3d` in a future major version release.
