Return the statistic function of a `BootstrapSample`

```julia
bs = bootstrap(mean, randn(20), BasicSampling(100))
statistic(bs)
```
