```
heteropca(X, rank=size(X, 1); kwargs...)
```

Convenience wrapper for `fit(HeteroPCAModel, X, rank=size(X, 1); kwargs...)`.

# Arguments

  * `X::AbstractMatrix{T}`: The input data matrix of dimension `d × n`
  * `rank::Int=size(X, 1)`: The target dimensionality *k* (number of components to extract)

# Keyword arguments

  * `maxiter::Int=1_000`: Maximum number of iterations for the algorithm
  * `abstol::Float64=1e-6`: Convergence tolerance for diagonal estimation
  * `demean::Bool=true`: Whether to center the data by subtracting column means; if the model is already demeaned, set `demean=false`
  * `impute_method::Symbol=:pairwise`: Method for handling missing values (:pairwise or :zero); `impute = :pairwise` compute the pairwise covariance matrix using available data only; `impute = :zero` fills the missing values with zeros after demeaning, and compute the covariance matrix adjusted for the sample missing rate.
  * `alpha::Float64=1.0`: Diagonal update relaxation parameter; `alpha = 1` reproduces the original scheme;
