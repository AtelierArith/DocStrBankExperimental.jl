```
logabsbinomial(n, k)
```

大きな `n` と `k` が `n/2` に近い場合の `binomial` 係数 `binomial(n, k)` の絶対値の自然対数を正確に計算します。

タプル `(log(abs(binomial(n,k))), sign(binomial(n,k)))` を返します。

外部リンク [`Base.binomial`](https://docs.julialang.org/en/v1/base/math/#Base.binomial)
