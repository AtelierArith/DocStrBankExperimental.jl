ブートストラップサンプリングのバイアスを推定します。

```julia
bs = bootstrap(mean, randn(20), BasicSampling(100))

bias(bs)
```
