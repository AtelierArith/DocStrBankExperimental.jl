```
hwfilter(x::Array)
```

Filter a time series `x` using the harmonically weighted filter.

# Arguments

  * `x::Vector`: time series

# Output

  * `hwx::Vector`: filtered time series

# Notes

The harmonically weighted filter is computed using the fast Fourier transform.

# Examples

```julia-repl
julia> hwfilter(randn(100,1))
```
