```
nsamples(F::SampledSystem) -> Int
```

Returns the number of samples of `F`. Notice that `ninstances(F)*nsolutions(F)` doesn't have to be equal to `nsamples(F)`.
