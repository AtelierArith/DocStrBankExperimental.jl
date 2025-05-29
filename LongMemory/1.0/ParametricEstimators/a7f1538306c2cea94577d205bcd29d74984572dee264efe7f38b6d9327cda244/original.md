```
csa_var_matrix(T::Int, d::Real)
```

Constructs the autocovariance matrix of the CSA process with parameters`p` and `q` at lags 0, 1, ..., `T-1`.

# Arguments

  * `T::Int`: The number of lags to compute.
  * `p::Real`: The first parameter of the CSA process.
  * `q::Real`: The second parameter of the CSA process.

# Output

  * `V::Array`: The autocovariance matrix of the CSA process with parameters `p` and `q` at lags 0, 1, ..., `T-1`.

# Examples

```julia
julia> csa_var_matrix(10, 1.4, 1.8)
```
