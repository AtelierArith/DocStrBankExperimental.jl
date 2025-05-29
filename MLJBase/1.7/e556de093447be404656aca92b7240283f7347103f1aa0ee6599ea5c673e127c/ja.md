```
Distributions.fit(D, r::MLJBase.NumericRange)
```

分布 `d` をタイプ `D` にフィットさせ、1次元の範囲 `r` を返します。

以下の表に示すタイプ `D` のみがサポートされています。

分布 `d` は2段階で構築されます。まず、表の2列目の条件によって特徴付けられる分布 `d0` が `r` にフィットします。次に、`d0` を `r.lower` と `r.upper` の間で切り詰めて `d` を得ます。

| 分布タイプ `D`                                                                                    | `d0` の特徴付け                                               |
|:-------------------------------------------------------------------------------------------- |:-------------------------------------------------------- |
| `Arcsine`, `Uniform`, `Biweight`, `Cosine`, `Epanechnikov`, `SymTriangularDist`, `Triweight` | `minimum(d) = r.lower`, `maximum(d) = r.upper`           |
| `Normal`, `Gamma`, `InverseGaussian`, `Logistic`, `LogNormal`                                | `mean(d) = r.origin`, `std(d) = r.unit`                  |
| `Cauchy`, `Gumbel`, `Laplace`, (`Normal`)                                                    | `Dist.location(d) = r.origin`, `Dist.scale(d)  = r.unit` |
| `Poisson`                                                                                    | `Dist.mean(d) = r.unit`                                  |

ここで `Dist = Distributions` です。
