```
constant_1d(; seed=nothing, value=0.0)
```

Construct a sampler that constantly outputs `value` each time it is sampled from.

This is useful for debugging and applications where you need to combine a constant value.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
  * `value`: A constant value to emit each time this sampler is sampled from.
