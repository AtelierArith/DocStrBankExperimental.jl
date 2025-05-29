```
get_dist_error(dist_params::Vector{Float64})
get_dist_error(dist_params::Vector{Float64}, dist_params_cov::Matrix{Float64})
```

Returns the error suppression factor, the change in error rate in a code as the distance is increased by 2, determined from `dist_params`, and its standard error if its covariance matrix `dist_params_cov` is supplied.
