```
sample([rng], domain, size, [weights]; replace=false, ordered=false)
```

Utility method that calls the `sample` function using `WeightedSampling(size, weights; replace, ordered)`. If `weights` is not defined, this is equivalent to using `UniformSampling(size; replace, ordered)`.
