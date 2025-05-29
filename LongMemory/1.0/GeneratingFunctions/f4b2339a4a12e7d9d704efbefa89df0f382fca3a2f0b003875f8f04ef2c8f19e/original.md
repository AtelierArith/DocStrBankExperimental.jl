```
fracdiff(x,d)
```

Compute the fractional difference of a time series `x` with fractional order `d∈(-1/2,1/2)`.

# Arguments

  * `x::Vector`: time series
  * `d::Float64`: fractional difference parameter

# Output

  * `dx::Vector`: fractional difference of `x`

# Notes

The function uses the fast Fourier transform to compute the convolution of the time series with the fractional difference filter.  See [Jensen and Nielsen (2014)](https://onlinelibrary.wiley.com/doi/10.1111/jtsa.12074) for details. We use autoregressive formulas to efficiently compute the coefficients of the fractional difference filter.

# Examples

```julia-repl
julia> fracdiff(randn(100,1),0.4)
```
