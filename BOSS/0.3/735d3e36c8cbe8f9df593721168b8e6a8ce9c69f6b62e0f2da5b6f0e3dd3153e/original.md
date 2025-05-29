```
model_posterior_slice(::BossProblem, slice::Int) -> post
```

Return the posterior predictive distributions of the given output `slice` with two methods:

  * `post(x::AbstractVector{<:Real}) -> μ::Real, σ::Real`
  * `post(X::AbstractMatrix{<:Real}) -> μ::AbstractVector{<:Real}, Σ::AbstractMatrix{<:Real}`

The first method takes a single point `x` of length `x_dim(::BossProblem)` from the `Domain`, and returns the predictive mean and deviation of the corresponding output number `y` such that:

  * `μ, σ = post(x)` => `y ∼ Normal(μ, σ)`

The second method takes multiple points from the `Domain as a column-wise matrix`X`of size`(x_dim, N)`, and returns the joint predictive mean and covariance matrix of the corresponding output vector`y`of length`N` such that:

  * `μ, Σ = post(X)` => `y ∼ MvNormal(μ, Σ)`

In case one is only interested in predicting a certain output dimension, using `model_posterior_slice` can be more efficient than `model_posterior` (depending on the used `SurrogateModel`).

Note that `model_posterior_slice` can be used even if `sliceable(model) == false`. It will, however, not provide any additional efficiency in such case.

See also: [`model_posterior`](@ref)
