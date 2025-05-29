```
whittle_est(x::Array; m::Real=0.8, l=0)
```

Estimate the long memory parameter of a time series `x` using the Whittle log-likelihood function. See Künsch (1987) for details.

# Arguments

  * `x::Vector`: time series
  * `m∈(0,1)::Float64`: taper final
  * `l∈(0,1)::Float64`: taper initial

# Output

  * `d::Float64`: long memory parameter

# Notes

The function considers the periodogram of the time series `x` for frequencies in the interval `[T^l,T^m]`. The zero frequency is always excluded. The condition `m < l` must hold. The default values of `m` and `l` are 0.8 and 0, respectively.

# Examples

```julia-repl
julia> whittle_est(randn(100,1))
```
