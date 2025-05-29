```
dic(loglik::AbstractVector{<:Real})
```

Compute the Deviance Information Criterion (DIC).

# Arguments

  * `loglik::AbstractArray`: A vector of posterior log likelihoods

# Returns

  * `dic::Real`: DIC value

Note: DIC assumes that the posterior distribution is approx. multivariate Gaussian and tends to select overfitted models.
