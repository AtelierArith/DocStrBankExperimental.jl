```
get_round_error(round_params::Vector{Float64})
get_round_error(round_params::Vector{Float64}, round_params_cov::Matrix{Float64})
```

Returns the error per round determined from `round_params`, and its standard error if its covariance matrix `round_params_cov` is supplied.
