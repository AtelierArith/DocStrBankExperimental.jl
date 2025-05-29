```
KmeansAlg(m::Int, metric::SemiMetric=SqEuclidean(); nMarkov = 10, tol = 1e-3)
```

k-Means [1] の初期化は、`X` データに対して `m` の誘導点を取ります。シーディングは [2] によって計算され、`nMarkov` はシーディングのための MCMC ステップの数を示します。

## 引数

  * `k::Int` : 誘導点の数
  * `metric::SemiMetric` : k-means アルゴリズムの距離を計算するために使用されるメトリック

## キーワード引数

  * `nMarkov::Int` : シーディングのためのランダムステップの数
  * `tol::Real` : `kmeans` アルゴリズムの許容誤差

[1] Arthur, D. & Vassilvitskii, S. k-means++: The advantages of careful seeding. in Proceedings of the eighteenth annual ACM-SIAM symposium on Discrete algorithms 1027–1035 (Society for Industrial and Applied Mathematics, 2007). [2] Bachem, O., Lucic, M., Hassani, S. H. & Krause, A. Fast and Provably Good Seedings for k-Means. Advances in Neural Information Processing Systems 29 55–63 (2016) doi:10.1109/tmtt.2005.863818.
