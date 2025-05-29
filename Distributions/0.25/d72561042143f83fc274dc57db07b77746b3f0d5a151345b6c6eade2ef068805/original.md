```
product_distribution(dists::AbstractVector{<:Normal})
```

Create a multivariate normal distribution by stacking the univariate normal distributions.

The resulting distribution of type [`MvNormal`](@ref) has a diagonal covariance matrix.
