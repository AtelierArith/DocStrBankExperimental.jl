```
fit_mle(dists::ArrayOfUnivariateDistribution, x::AbstractArray)
fit_mle(dists::ArrayOfUnivariateDistribution, x::AbstractArray, γ::AbstractVector)
```

The `fit_mle` for a `ArrayOfUnivariateDistribution` distributions `dists` is the `product_distribution` of `fit_mle` of each components of `dists`. `VectorOfUnivariateDistribution` should act like old `Product` while `ArrayOfUnivariateDistribution` are not really tested yet.
