```
simulate_random_response(x, k, traits)
```

Simulates a response matrix `Y` where each row is an independent multivariate Gaussian with length `trait`. There are `k` non-zero `β` over all traits. Each trait shares `overlap` causal SNPs. The covariance matrix `Σ` is positive definite and symmetric.

# Arguments

  * `x`: Design matrix of dimension `n × p`. Each row is a sample.
  * `k`: the total true number of causal SNPs (predictors)
  * `traits`: Number of traits

# Optional arguments

  * `Zu`: Effect of non-genetic covariates. `Zu` should have dimension `n × traits`.
  * `overlap`: Number of causal SNPs shared by all traits. Shared SNPs does not have the same effect size.

# Outputs

  * `Y`: Response matrix where each row is sampled from a multivariate normal with mean `μ[i] = X[i, :] * true_b` and variance `Σ`
  * `Σ`: the symmetric, positive definite covariance matrix used
  * `true_b`: A sparse matrix containing true beta values.
  * `correct_position`: Non-zero indices of `true_b`
