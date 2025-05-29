Estimate the standard error of a bootstrap sampling.

```julia
bs = bootstrap(mean, randn(20), BasicSampling(100))

stderror(bs)
```
