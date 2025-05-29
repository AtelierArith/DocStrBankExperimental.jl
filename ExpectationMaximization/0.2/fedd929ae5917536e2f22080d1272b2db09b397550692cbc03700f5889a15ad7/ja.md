```
fit_mle(dists::ArrayOfUnivariateDistribution, x::AbstractArray)
fit_mle(dists::ArrayOfUnivariateDistribution, x::AbstractArray, γ::AbstractVector)
```

`ArrayOfUnivariateDistribution` 分布 `dists` の `fit_mle` は、`dists` の各コンポーネントの `fit_mle` の `product_distribution` です。`VectorOfUnivariateDistribution` は古い `Product` のように動作する必要がありますが、`ArrayOfUnivariateDistribution` はまだ十分にテストされていません。
