```
reservoir_sample_without_replacement(rng, iter, n; ordered = false, method = :alg_L)
```

Reservoir sampling algorithm without replacement. The `method` keyword can be either `:alg_L` or `:alg_R`.

Adapted from algorithms R and L described in "Random sampling with a reservoir, J. S. Vitter, 1985".
