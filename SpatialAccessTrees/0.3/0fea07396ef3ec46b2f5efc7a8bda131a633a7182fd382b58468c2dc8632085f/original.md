```
BeamSearchSat(sat::Sat; bsize=8, Δ=1f0)
```

Creates an approximate similarity sarch index based on sat and aggressive pruning; adapted from the paper *A probabilistic spell for the curse of dimensionality* (Chavez and Navarro, 2001). It supports auto-tuning via  [`optimize!`](@ref).
