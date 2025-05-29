```
weighted_reservoir_sample_with_replacement(rng, iter, wv, n; ordered = false)
```

Weighted reservoir sampling algorithm without replacement. `wv` should be a function  which accept an element of the iterator and returns a `Float64`.

Adapted from algorithm WRSWR_SKIP described in "A Skip-based Algorithm for Weighted Reservoir  Sampling with Replacement, A. Meligrana, 2024". 
