```
bic(max_loglike, k, n)
```

Computes the Bayesian Information Criterion (BIC).

# Arguments

  * `max_loglike`: the log likelihood evaluated at the maximum likelihood estimate
  * `k`: the number of parameters in the model
  * `n`: the number of observations in the data

# Returns

  * `bic::Real`: BIC value
