```
gph_est_variance(T::Int; m::Real=0.8, l=0, br=0::Int)
```

Estimate the variance of the long memory parameter of a time series of length `T` using the log-periodogram estimator. See [Geweke and Porter-Hudak (1983)](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9892.1983.tb00371.x) and [Andrews and Guggenberger (2003)](https://www.jstor.org/stable/3082070) for details.

# Arguments

  * `T::Int`: length of the time series

# Optional arguments

  * `m∈(0,1)::Float64`: taper final. Default is 0.8
  * `br::Int64`: number of bias reduction terms

# Output

  * `varb::Float64`: variance of the long memory parameter

# Notes

Multiple dispatch is used for computation. If the first input is an integer, the function interprets it as the sample size; otherwise, it computes the sample size from the length of the time series.

# Examples

```julia-repl
julia> gph_est_variance(100,0.4)
```
