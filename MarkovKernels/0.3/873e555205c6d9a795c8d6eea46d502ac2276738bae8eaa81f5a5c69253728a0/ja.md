```
posterior_and_loglike(D::AbstractDistribution, K::AbstractMarkovKernel, y)
```

事前分布 D、測定カーネル K、および測定 y に関連する条件付き分布 C と周辺対数尤度 ℓ を計算します。
