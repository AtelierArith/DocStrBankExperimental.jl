```
estimate_parameters(k::Integer, shared_cov::Matrix{Float64}, first::Vector{Float64}, second::Matrix{Float64}; method = "recursive")
```

Compute an estimate for the means of a Gaussian `k`-mixture model with equal mixing coefficients and known shared covariances from the moments.

The shared covariance matrix `shared_cov` will determine the dimension. Then `first` should be a list of moments 0 through k for the first dimension, `second` should be a matrix of moments $m_{je_1+e_i}$ for j in 0 to `k`-1 and i in 2 to d as a matrix where d is the dimension, i varies across rows, and j varies down columns.
