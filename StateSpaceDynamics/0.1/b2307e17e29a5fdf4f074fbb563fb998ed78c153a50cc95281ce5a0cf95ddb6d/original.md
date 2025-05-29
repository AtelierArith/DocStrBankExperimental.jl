```
loglikelihood(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat})
```

Calculate the log-likelihood of the data given the PPCA model.

# Args:

  * `model::ProbabilisticPCA`: PPCA model
  * `X::Matrix{<:AbstractFloat}`: Data matrix

# Examples:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
loglikelihood(ppca, rand(10, 2))
```
