```
fit_expdecay(lags, acf; dims=ndims(acf))
```

Fit exponential decay to autocorrelation function.

# Arguments

  * `lags::AbstractVector{T}`: Time lags
  * `acf::AbstractArray{T}`: Autocorrelation values
  * `dims::Int=ndims(acf)`: Dimension along which to fit

# Returns

  * Fitted timescale parameter(s)

# Notes

  * Uses NonlinearSolve.jl with FastShortcutNLLSPolyalg
  * Initial guess based on ACW50
