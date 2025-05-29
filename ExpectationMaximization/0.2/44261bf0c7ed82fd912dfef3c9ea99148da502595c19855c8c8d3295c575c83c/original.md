```
fit_mle(g::Product, x::AbstractMatrix)
fit_mle(g::Product, x::AbstractMatrix, γ::AbstractVector)
```

The `fit_mle` for multivariate Product distributions `g` is the `product_distribution` of `fit_mle` of each components of `g`. Product is meant to be depreacated in next versions of `Distribution.jl`. Use the analog `VectorOfUnivariateDistribution` type instead.
