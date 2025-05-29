```julia
nancov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

Compute the covariance matrix of the matrix `X`, along dimension `dims`. As `Statistics.cov`, but ignoring `NaN`s.

If `corrected` is `true` as is the default, *Bessel's correction* will be applied, such that the sum is scaled by `n-1` rather than `n`, where `n = length(x)`.
