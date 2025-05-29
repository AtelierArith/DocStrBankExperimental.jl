`BootstrapSample`の統計関数を返します

```julia
bs = bootstrap(mean, randn(20), BasicSampling(100))
statistic(bs)
```
