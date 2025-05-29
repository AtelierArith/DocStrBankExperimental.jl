```
log_likelihood(cov, τ, y, σ2)
```

Compute the log-likelihood of a semi-separable covariance function using the celerite algorithm.

# Arguments

  * `cov::SumOfSemiSeparable` or `cov::CARMA` or `cov::SemiSeparable`: the covariance function
  * `τ::Vector`: the time points
  * `y::Vector`: the data
  * `σ2::Vector`: the measurement variances
