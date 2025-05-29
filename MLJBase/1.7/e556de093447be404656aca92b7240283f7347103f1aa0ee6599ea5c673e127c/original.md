```
Distributions.fit(D, r::MLJBase.NumericRange)
```

Fit and return a distribution `d` of type `D` to the one-dimensional range `r`.

Only types `D` in the table below are supported.

The distribution `d` is constructed in two stages. First, a distributon `d0`, characterized by the conditions in the second column of the table, is fit to `r`. Then `d0` is truncated between `r.lower` and `r.upper` to obtain `d`.

| Distribution type `D`                                                                        | Characterization of `d0`                                 |
|:-------------------------------------------------------------------------------------------- |:-------------------------------------------------------- |
| `Arcsine`, `Uniform`, `Biweight`, `Cosine`, `Epanechnikov`, `SymTriangularDist`, `Triweight` | `minimum(d) = r.lower`, `maximum(d) = r.upper`           |
| `Normal`, `Gamma`, `InverseGaussian`, `Logistic`, `LogNormal`                                | `mean(d) = r.origin`, `std(d) = r.unit`                  |
| `Cauchy`, `Gumbel`, `Laplace`, (`Normal`)                                                    | `Dist.location(d) = r.origin`, `Dist.scale(d)  = r.unit` |
| `Poisson`                                                                                    | `Dist.mean(d) = r.unit`                                  |

Here `Dist = Distributions`.
