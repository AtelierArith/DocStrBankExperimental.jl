ブートストラップサンプリングの標準誤差を推定します。

```julia
bs = bootstrap(mean, randn(20), BasicSampling(100))

stderror(bs)
```
