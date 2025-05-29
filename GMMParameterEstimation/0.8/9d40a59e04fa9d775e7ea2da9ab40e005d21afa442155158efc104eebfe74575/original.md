```
estimate_parameters(d::Integer, k::Integer, first::Vector{Float64}, second::Matrix{Float64})
```

Compute an estimate for the parameters of a `d`-dimensional Gaussian `k`-mixture model from the moments.

For the unknown mixing coefficient diagonal covariance matrix case, `first` should be a list of moments 0 through 3k for the first dimension, and `second` should be a matrix of moments 1 through 2k+1 for the remaining dimensions.
