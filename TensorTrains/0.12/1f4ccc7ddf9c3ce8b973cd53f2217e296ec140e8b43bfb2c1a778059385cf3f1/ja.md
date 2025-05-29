```
twovar_marginals(A::AbstractTensorTrain; l, r, M, Δlmax)
```

各サイトのペアに対する周辺分布 $p(x^l, x^m)$ を計算します。

### オプション引数

  * `l = accumulate_L(A)[1]`, `r = accumulate_R(A)[1]`, `M = accumulate_M(A)` 事前計算された部分正規化
  * `maxdist = length(A)`: 距離 `maxdist` でのみ周辺分布を計算します: $|l-m|\le maxdist$
