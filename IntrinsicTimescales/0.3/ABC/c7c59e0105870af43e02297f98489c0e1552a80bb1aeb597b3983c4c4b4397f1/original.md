```
ABCResults
```

Container for ABC results to standardize plotting interface.

# Fields

  * `theta_history::Vector{Matrix{Float64}}`: History of parameter values across iterations
  * `epsilon_history::Vector{Float64}`: History of epsilon values
  * `acc_rate_history::Vector{Float64}`: History of acceptance rates
  * `weights_history::Vector{Vector{Float64}}`: History of weights
  * `final_theta::Matrix{Float64}`: Final accepted parameter values
  * `final_weights::Vector{Float64}`: Final weights
