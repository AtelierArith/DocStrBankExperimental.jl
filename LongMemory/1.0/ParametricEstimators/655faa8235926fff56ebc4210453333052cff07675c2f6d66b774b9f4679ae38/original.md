```
fi_llk(d::Real, x::Array)
```

Computes the log-likelihood of the fractional differenced process with parameter `d` given the data `x`.

# Arguments

  * `d::Real`: The fractional differencing parameter.
  * `x::Array`: The data.

# Output

  * `llk::Real`: The log-likelihood of the fractional differenced process with parameter `d` given the data `x`.

# Notes

This function computes the concentrated log-likelihood function of the fractional differenced process with parameter `d` given the data `x`.

# Examples

```julia
julia> fi_llk(0.4, randn(100,1))
```
