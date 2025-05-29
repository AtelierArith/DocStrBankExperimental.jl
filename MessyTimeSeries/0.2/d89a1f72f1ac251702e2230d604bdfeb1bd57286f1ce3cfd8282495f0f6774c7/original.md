```
rand_without_replacement(rng::StableRNGs.LehmerRNG, n::Int64, T::Int64, d::Int64)
```

Draw `length(P)-d` elements from the positional vector `P` without replacement. 

In the sampling process, no more than n-1 elements are removed for each point in time. `P` is permanently changed in the process.
