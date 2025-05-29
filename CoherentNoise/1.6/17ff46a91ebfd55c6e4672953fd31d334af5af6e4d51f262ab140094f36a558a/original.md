```
opensimplex2_2d(; seed=nothing, orient=nothing)
```

Construct a sampler that outputs 2-dimensional OpenSimplex2 noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
  * `orient`: Either the symbol `:x` or the value `nothing`:

      * `nothing`: Use the standard orientation.
      * `:x`: The noise space will be re-oriented with the Y axis pointing down the main diagonal to improve visual isotropy.
