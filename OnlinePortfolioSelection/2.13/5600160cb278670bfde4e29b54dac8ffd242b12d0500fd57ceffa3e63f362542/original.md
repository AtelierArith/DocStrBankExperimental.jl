```
OPSAlgorithm{T<:AbstractFloat}
```

An object that contains the result of running the algorithm.

# Fields

  * `n_asset::Int`: Number of assets in the portfolio.
  * `b::Matrix{T}`: Weights of the created portfolios.
  * `alg::String`: Name of the algorithm.
