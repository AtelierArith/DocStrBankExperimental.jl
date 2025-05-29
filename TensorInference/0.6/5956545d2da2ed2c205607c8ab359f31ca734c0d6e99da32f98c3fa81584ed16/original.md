```julia
sample(
    tn::TensorInference.TensorNetworkModel,
    n::Int64;
    usecuda,
    queryvars
) -> TensorInference.Samples{Int64}

```

Generate samples from a tensor network based probabilistic model. Returns a vector of vector, each element being a configurations defined on `get_vars(tn)`.

### Arguments

  * `tn` is the tensor network model.
  * `n` is the number of samples to be returned.

### Keyword Arguments

  * `usecuda` is a boolean flag to indicate whether to use CUDA for tensor computation.
  * `queryvars` is the variables to be sampled, default is `get_vars(tn)`.
