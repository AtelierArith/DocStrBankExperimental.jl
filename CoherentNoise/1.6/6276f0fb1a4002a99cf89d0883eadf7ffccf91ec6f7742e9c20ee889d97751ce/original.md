```
perlin_2d(; seed=nothing)
perlin_improved_2d(; seed=nothing)
```

Construct a sampler that outputs 2-dimensional Perlin "Improved" noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.

# Notes:

  * `perlin_improved_2d` is deprecated and will be removed in favor of `perlin_2d` in a future major version release.
