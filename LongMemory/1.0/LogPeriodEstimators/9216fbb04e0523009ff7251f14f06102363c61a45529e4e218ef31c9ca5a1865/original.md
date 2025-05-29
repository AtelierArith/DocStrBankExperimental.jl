```
exact_whittle_est_variance(x::Array; m::Real=0.8)
```

Estimate the variance of the estimator for the long memory parameter of a time series `x` using the exact Whittle log-likelihood function. 

# Arguments

  * `x::Vector`: time series

# Optional arguments

  * `m∈(0,1)::Float64`: taper final. Default is 0.8

# Output

  * `varb::Float64`: variance of the estimator

# Notes

Multiple dispatch is used for computation. If the first input is an integer, the function interprets it as the sample size; otherwise, it computes the sample size from the length of the time series. The variance is the same as the one from using the Whittle log-likelihood function.

# Examples

```julia-repl
julia> exact_whittle_est_variance(fi(100,0.4))
```
