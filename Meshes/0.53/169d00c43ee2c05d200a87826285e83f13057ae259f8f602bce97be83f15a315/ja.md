```
sample([rng], domain, size, [weights]; replace=false, ordered=false)
```

`sample` 関数を `WeightedSampling(size, weights; replace, ordered)` を使用して呼び出すユーティリティメソッドです。`weights` が定義されていない場合、これは `UniformSampling(size; replace, ordered)` を使用することと同等です。
