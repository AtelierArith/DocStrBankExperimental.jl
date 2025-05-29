```julia
vcov(x::AbstractVector, y::AbstractVector; corrected::Bool=true, multithreaded=false)
```

Compute the covariance between the vectors `x` and `y`. As `Statistics.cov`, but vectorized and (optionally) multithreaded.

If `corrected` is `true` as is the default, *Bessel's correction* will be applied, such that the sum is scaled by `n-1` rather than `n`, where `n = length(x)`.
