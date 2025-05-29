```
sample(sampler)
```

Take a single random sample from `sampler`, returning the index of the element sampled.

Samples by inverse transform sampling (see `cdf_sample`(@ref)) to select a `FlexLevel` in `sampler`, then rejection sampling (see `rejection_sample`(@ref)) an index from said `FlexLevel`.
