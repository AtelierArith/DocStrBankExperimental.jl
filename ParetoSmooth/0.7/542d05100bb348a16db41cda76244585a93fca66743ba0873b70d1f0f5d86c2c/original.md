```
pointwise_log_likelihoods(
    ll_fun::Function, samples::AbstractArray{<:Real,3}, data;
    splat::Bool=true[, chain_index::Vector{<:Integer}]
)
```

Compute the pointwise log likelihoods.

# Arguments

  * `ll_fun::Function`: A function taking a single data point and returning the log-likelihood

of that point. This function must take the form `f(θ[1], ..., θ[n], data)`, where `θ` is the parameter vector. See also the `splat` keyword argument.

  * `samples::AbstractArray`: A three dimensional array of MCMC samples. Here, the first dimension should indicate the step of the MCMC algorithm; the second dimension should indicate the parameter; and the third should indicate the chain.
  * `data`: An array of data points used to estimate the parameters of the model.
  * `splat`: If `true` (default), `f` must be a function of `n` different parameters.  Otherwise, `f` is assumed to be a function of a single parameter vector.
  * `chain_index::Vector{Int}`: An optional vector of integers specifying which chain each step

belongs to. For instance, `chain_index[step]` should return `2` if `log_likelihood[:, step]` belongs to the second chain.

# Returns

  * `Array`: A three dimensional array of pointwise log-likelihoods.
