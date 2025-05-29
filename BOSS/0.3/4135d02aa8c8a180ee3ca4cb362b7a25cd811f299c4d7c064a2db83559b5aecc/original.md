```
model_posterior(::BossProblem) -> post
```

Return the posterior predictive distribution of the surrogate model with two methods:

  * `post(x::AbstractVector{<:Real}) -> μs::AbstractVector{<:Real}, σs::AsbtractVector{<:Real}`
  * `post(X::AbstractMatrix{<:Real}) -> μs::AbstractMatrix{<:Real}, Σs::AbstractArray{<:Real, 3}`

The first method takes a single point `x` of length `x_dim(::BossProblem)` from the `Domain`, and returns the predictive means and deviations of the corresponding output vector `y` of length `y_dim(::BossProblem)` such that:

  * `μs, σs = post(x)` => `y ∼ product_distribution(Normal.(μs, σs))`
  * `μs, σs = post(x)` => `y[i] ∼ Normal(μs[i], σs[i])`

The second method takes multiple points from the `Domain` as a column-wise matrix `X` of size `(x_dim, N)`, and returns the joint predictive means and covariance matrices of the corresponding output matrix `Y` of size `(y_dim, N)` such that:

  * `μs, Σs = post(X)` => `transpose(Y) ∼ product_distribution(MvNormal.(eachcol(μs), eachslice(Σs; dims=3)))`
  * `μs, Σs = post(X)` => `Y[i,:] ∼ MvNormal(μs[:,i], Σs[:,:,i])`

See also: [`model_posterior_slice`](@ref)
