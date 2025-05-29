```
exact_whittle_est(x::Array; m::Real=0.8, l=0, detrend = true)
```

Estimate the long memory parameter of a time series `x` using the exact Whittle log-likelihood function. See [Shimotsu and Phillips (2005)](https://doi.org/10.1214/009053605000000309) for details.

# Arguments

  * `x::Vector`: time series
  * `m∈(0,1)::Float64`: taper final
  * `l∈(0,1)::Float64`: taper initial
  * `detrend::Bool`: If true, the time series is demeaned before estimation.

# Output

  * `d::Float64`: long memory parameter

# Notes

The function considers the periodogram of the time series `x` for frequencies in the interval `[T^l,T^m]`. The zero frequency is always excluded. The condition `m < l` must hold. The default values of `m` and `l` are 0.8 and 0, respectively.

# Examples

```julia-repl
julia> exact_whittle_est(randn(100,1))
```
