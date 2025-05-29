```
csa_mle_est(x::Array)
```

Computes the maximum likelihood estimate of the parameters `p` and `q` of the CSA process and the standard deviation of the CSA process given the data `x`.

# Arguments

  * `x::Array`: The data.

# Output

  * `p::Real`: The maximum likelihood estimate of the first parameter of the CSA process.
  * `q::Real`: The maximum likelihood estimate of the second parameter of the CSA process.
  * `σ::Real`: The maximum likelihood estimate of the standard deviation of the CSA process.

# Notes

This function uses the `Optim` package to minimize the log-likelihood function.

# Examples

```julia
julia> csa_mle_est(randn(100,1))
```
