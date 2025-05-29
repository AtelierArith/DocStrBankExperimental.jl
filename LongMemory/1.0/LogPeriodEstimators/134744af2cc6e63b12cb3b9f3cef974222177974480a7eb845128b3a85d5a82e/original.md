```
gph_est(x::Array; m::Real=0.8, l=0, br=0::Int)
```

Estimate the long memory parameter of a time series `x` using the log-periodogram estimator. See [Geweke and Porter-Hudak (1983)](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9892.1983.tb00371.x) and [Andrews and Guggenberger (2003)](https://www.jstor.org/stable/3082070) for details.

# Arguments

  * `x::Vector`: time series
  * `m∈(0,1)::Float64`: taper final
  * `l∈(0,1)::Float64`: taper initial
  * `br::Int64`: number of bias reduction terms

# Output

  * `d::Float64`: long memory parameter

# Notes

The function considers the periodogram of the time series `x` for frequencies in the interval `[T^l,T^m]`. The zero frequency is always excluded. The default values of `m` and `l` are 0.8 and 0, respectively. The condition `m < l` must hold.

The default value of `br` is 0 which returns the original GPH log-periodogram estimator.

# Examples

```julia-repl
julia> gph_est(randn(100,1))
```
