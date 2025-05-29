```
simulate_random_response(x, k, d, l; kwargs...)
```

This function simulates a random response (trait) vector `y`. When the  distribution `d` is from Poisson, Gamma, or Negative Binomial, we simulate  `β ∼ N(0, 0.3)` to roughly ensure the mean of response `y` doesn't become too large. For other distributions, we choose `β ∼ N(0, 1)`. 

# Arguments

  * `x`: Design matrix
  * `k`: the true number of predictors.
  * `d`: The distribution of the simulated trait (note `typeof(d) = UnionAll` but `typeof(d())` is an actual distribution: e.g. Normal)
  * `l`: The link function. Input `canonicallink(d())` if you want to use the canonical link of `d`.

# Optional arguments

  * `r`: The number of success until stopping in negative binomial regression, defaults to 10
  * `α`: Shape parameter of the gamma distribution, defaults to 1
  * `Zu`: Effect of non-genetic covariates. `Zu` should have dimension `n × 1`.
