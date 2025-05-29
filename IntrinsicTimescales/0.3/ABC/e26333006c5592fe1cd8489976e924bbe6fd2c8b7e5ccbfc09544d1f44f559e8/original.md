```
pmc_abc(model::Models.AbstractTimescaleModel; epsilon_0=1.0, max_iter=10000, min_accepted=100, steps=10, sample_only=false, minAccRate=0.01, target_acc_rate=0.01)
```

Perform Population Monte Carlo Approximate Bayesian Computation (PMC-ABC) inference.

# Arguments

  * `model::Models.AbstractTimescaleModel`: Model to perform inference on
  * `epsilon_0::Float64=1.0`: Initial epsilon threshold for acceptance
  * `max_iter::Int=10000`: Maximum number of iterations per step
  * `min_accepted::Int=100`: Minimum number of accepted samples required
  * `steps::Int=10`: Number of PMC steps to perform
  * `sample_only::Bool=false`: If true, only perform sampling without adaptation
  * `minAccRate::Float64=0.01`: Minimum acceptance rate before stopping
  * `target_acc_rate::Float64=0.01`: Target acceptance rate for epsilon adaptation

# Returns

Vector of NamedTuples containing results for each PMC step, including:

  * Accepted parameters (theta_accepted)
  * Distances (D_accepted)
  * Number of accepted/total samples
  * Epsilon threshold
  * Sample weights
  * Covariance matrix (tau_squared)
  * Effective sample size
