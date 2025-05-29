```julia
nancovem(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

Compute the covariance-of-error-of-the-mean matrix `X`, along dimension `dims`, ignoring NaNs. That is, a matrix composed of the covariance of the error of the mean of the non-nan pairs of each column (dims=1) or row (dims=2) of the matrix `X`, where covariance of the error of the mean is to covariance  as standard error of the mean is to standard deviation.

If `corrected` is `true` as is the default, *Bessel's correction* will be applied, such that the sum is scaled by `n-1` rather than `n`, where `n = length(x)`.
