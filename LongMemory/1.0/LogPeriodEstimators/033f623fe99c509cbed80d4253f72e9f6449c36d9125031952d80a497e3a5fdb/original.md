```
periodogram(x::Array)
```

Compute the periodogram of a time series `x` using the fast Fourier transform.

# Arguments

  * `x::Vector`: time series

# Output

  * `I_w::Vector`: periodogram
  * `w::Vector`: Fourier frequencies

# Examples

```julia-repl
julia> periodogram(randn(100,1))
```
