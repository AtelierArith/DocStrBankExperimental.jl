```
fit!(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat}, max_iter::Int=100, tol::AbstractFloat=1e-6)
```

Fit the PPCA model to the data using the EM algorithm.

# Args:

  * `model::ProbabilisticPCA`: PPCA model
  * `X::Matrix{<:AbstractFloat}`: Data matrix
  * `max_iter::Int`: Maximum number of iterations
  * `tol::AbstractFloat`: Tolerance for convergence

# Examples:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
fit!(ppca, rand(10, 2))
```
