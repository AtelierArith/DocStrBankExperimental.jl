```
weighted_reservoir_sample_without_replacement(rng, iter, wv, n; ordered = false, method = :alg_AExpJ)
```

Weighted reservoir sampling algorithm without replacement. The `method` keyword can be  either `:alg_ARes` or `:alg_AExpJ`. `wv` should be a function which accept an element  of the iterator and returns a `Float64`.

Adapted from algorithm A-Res and A-ExpJ described in "Weighted random sampling with a reservoir,  P. S. Efraimidis et al., 2006". 
