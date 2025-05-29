```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}; is_sampling::Bool=false, is_return_log_prob::Bool=false)
```

This function is compatible with a multidimensional action space. To work with covariance matrices, the outputs are 3D tensors.  If sampling, return an actions tensor with dimensions `(action_size x action_samples x batchsize)` and a `logp_π` tensor with dimensions `(1 x action_samples x batchsize)`.  If not sampling, returns `μ` with dimensions `(action_size x 1 x batchsize)` and `L`, the lower triangular of the cholesky decomposition of the covariance matrix, with dimensions `(action_size x action_size x batchsize)` The covariance matrices can be retrieved with `Σ = stack(map(l -> l*l', eachslice(L, dims=3)); dims=3)`

  * `rng::AbstractRNG=Random.default_rng()`
  * `is_sampling::Bool=false`, whether to sample from the obtained normal distribution.
  * `is_return_log_prob::Bool=false`, whether to calculate the conditional probability of getting actions in the given state.
