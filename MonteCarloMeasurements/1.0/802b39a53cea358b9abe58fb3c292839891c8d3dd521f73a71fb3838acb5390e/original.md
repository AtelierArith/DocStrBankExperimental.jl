```
systematic_sample([rng::AbstractRNG,] N, d=Normal(0,1); permute=true)
```

returns a `Vector` of length `N` sampled systematically from the distribution `d`. If `permute=false`, this vector will be sorted.
