```
checkered_2d(; seed=nothing)
```

Construct a sampler that outputs values in a checkerboard-like pattern when it is sampled from.

That is, output values will only ever be -1.0 or 1.0.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
