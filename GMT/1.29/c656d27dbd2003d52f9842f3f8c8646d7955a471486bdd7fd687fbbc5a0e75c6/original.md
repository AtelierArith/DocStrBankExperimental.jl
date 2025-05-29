```
xcov(x::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

Compute the autocovariance of a vector or matrix x optionally specifying the lags at which to compute the autocovariance.

If x is a vector, return a vector of the same length as lags. If x is a matrix, return a matrix of size (length(lags), size(x,2)), where each column in the result corresponds to a column in x.

The output is not normalized. See `xcorr` for a function with normalization.
