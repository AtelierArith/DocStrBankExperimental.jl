```
KmeansAlg(m::Int, metric::SemiMetric=SqEuclidean(); nMarkov = 10, tol = 1e-3)
```

k-Means [1] initialization on the data `X` taking `m` inducing points. The seeding is computed via [2], `nMarkov` gives the number of MCMC steps for the seeding.

## Arguments

  * `k::Int` : Number of inducing points
  * `metric::SemiMetric` : Metric used to compute the distances for the k-means algorithm

## Keyword Arguments

  * `nMarkov::Int` : Number of random steps for the seeding
  * `tol::Real` : Tolerance for the `kmeans` algorithm

[1] Arthur, D. & Vassilvitskii, S. k-means++: The advantages of careful seeding. in Proceedings of the eighteenth annual ACM-SIAM symposium on Discrete algorithms 1027–1035 (Society for Industrial and Applied Mathematics, 2007). [2] Bachem, O., Lucic, M., Hassani, S. H. & Krause, A. Fast and Provably Good Seedings for k-Means. Advances in Neural Information Processing Systems 29 55–63 (2016) doi:10.1109/tmtt.2005.863818.
