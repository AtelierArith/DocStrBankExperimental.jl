```
fi_ar_coefs(d::Real, maxlags::Int)
```

Computes the AR coefficients of the fractional differenced process with parameter `d` at lags 1, ..., `maxlags`.

# Arguments

  * `d::Real`: The fractional differencing parameter.
  * `maxlags::Int`: The number of lags to compute.

# Output

  * `ar_coefs::Array`: The AR coefficients of the fractional differenced process with parameter `d` at lags 1, ..., `maxlags`.

# Notes

The AR coefficients are computed using the recursive formula for speed. The zero lag coefficient is not computed, it is theoretically 1.

# Examples

```julia
julia> fi_ar_coefs(0.2, 5)
```
