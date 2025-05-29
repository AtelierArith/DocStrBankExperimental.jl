```
find_MAP(theta_accepted::Matrix{Float64}, N::Int)
```

Find the MAP estimates from posteriors with grid search.

# Arguments

  * `theta_accepted::Matrix{Float64}`: Matrix of accepted samples from the final step of ABC
  * `N::Int`: Number of samples for grid search

# Returns

  * `theta_map::Vector{Float64}`: MAP estimates of the parameters
