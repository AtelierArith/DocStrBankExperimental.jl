```
perlin_4d(; seed=nothing)
perlin_improved_4d(; seed=nothing)
```

Construct a sampler that outputs 4-dimensional Perlin "Improved" noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.

# Notes:

  * `perlin_improved_4d` is deprecated and will be removed in favor of `perlin_4d` in a future major version release.
