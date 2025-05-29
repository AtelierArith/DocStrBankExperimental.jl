```julia
nancovem(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

Compute the covariance of the error of the mean of the non-nan pairs of `x` and `y`, where covariance of the error of the mean is to covariance  as standard error of the mean is to standard deviation.

If `corrected` is `true` as is the default, *Bessel's correction* will be applied, to the covariance, such that the sum is scaled by `n-1` rather than `n`, where `n = length(x)`.
