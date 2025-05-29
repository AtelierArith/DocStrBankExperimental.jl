```
estimate_parameters_weights_known(d::Integer, k::Integer, w::Array{Float64}, first::Matrix{Float64}, last::Dict{Vector{Int64}, Float64}; method = "recursive")
```

Compute an estimate for the parameters of a `d`-dimensional Gaussian `k`-mixture model from the moments.

For the known mixing coefficient general covariance matrix case, `w` should be a vector of the mixing coefficients `first` should be a list of moments 0 through 3k for the first dimension, `second` should be a matrix of moments 1 through 2k+1 for the remaining dimensions, and `last` should be a dictionary of the indices as lists of integers and the corresponding moments.
