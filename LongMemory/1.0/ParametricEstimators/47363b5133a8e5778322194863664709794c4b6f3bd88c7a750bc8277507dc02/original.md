```
fi_mle_est(x::Array)
```

Computes the maximum likelihood estimate of the fractional differencing parameter and the standard deviation of the fractional differenced process given the data `x`.

# Arguments

  * `x::Array`: The data.

# Output

  * `d::Real`: The maximum likelihood estimate of the fractional differencing parameter.
  * `σ::Real`: The maximum likelihood estimate of the standard deviation of the fractional differenced process.

# Notes

This function uses the `Optim` package to minimize the log-likelihood function.

# Examples

```julia
julia> fi_mle_est(randn(100,1))
```
