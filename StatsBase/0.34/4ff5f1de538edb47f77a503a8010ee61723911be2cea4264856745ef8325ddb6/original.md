```
scattermat(X, [wv::AbstractWeights]; mean=nothing, dims=1)
```

Compute the scatter matrix, which is an unnormalized covariance matrix. A weighting vector `wv` can be specified to weight the estimate.

# Arguments

  * `mean=nothing`: a known mean value. `nothing` indicates that the mean is unknown, and the function will compute the mean. Specifying `mean=0` indicates that the data are centered and hence there's no need to subtract the mean.
  * `dims=1`: the dimension along which the variables are organized. When `dims = 1`, the variables are considered columns with observations in rows; when `dims = 2`, variables are in rows with observations in columns.
