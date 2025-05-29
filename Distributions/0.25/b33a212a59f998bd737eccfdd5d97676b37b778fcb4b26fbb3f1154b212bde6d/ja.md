```
rand(rng::AbstractRNG, d::UnivariateDistribution)
```

`d`からスカラーサンプルを生成します。一般的なフォールバックは`quantile(d, rand())`です。
