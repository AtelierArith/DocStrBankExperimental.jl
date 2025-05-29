```
MinkowskiMetric <: Metric
```

ミンコフスキー計量は、次の式によって定義される計量です：

`d(x, y) = sum(w .* (x - y) .^ p) ^ (1 / p)`

ここで、`p` パラメータは計量を定義し、`w` は潜在的な重みベクトル（デフォルトではすべて1）です。

一般的なミンコフスキー計量：

  * `Cityblock`/`WeightedCityblock`: `p=1` のミンコフスキー計量；
  * `Euclidean`/`WeightedEuclidean`: `p=2` のミンコフスキー計量；
  * `Chebyshev`: `p` が無限大に近づくときの `d` の限界；
  * `Minkowski`/`WeightedMinkowski`: 任意の `p` に対する一般的なミンコフスキー計量。

## 注意事項

  * `Minkowski`/`WeightedMinkowski` と `MinkowskiMetric` の違いは、前者が一般的なミンコフスキー計量であるのに対し、後者はこれらの計量の親タイプであることです。
