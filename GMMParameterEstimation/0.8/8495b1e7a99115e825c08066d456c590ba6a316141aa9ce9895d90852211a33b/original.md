```
estimate_parameters_weights_known(d::Integer, k::Integer, w::Array{Float64}, moments::Matrix{Float64})
```

Compute an estimate for the parameters of a `d`-dimensional Gaussian `k`-mixture model from the moments.

For the known mixing coefficient diagonal covariance matrix case, `w` should be a vector of the mixing coefficients, and `moments` should be a matrix of moments 1 through 2k+1 for all dimensions.
