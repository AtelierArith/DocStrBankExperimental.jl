```
log_likelihood(pmm::PoissonMixtureModel, data::Matrix{Int})
```

Compute the log-likelihood of the data given the Poisson Mixture Model (PMM). The data matrix should be of shape (# observations, # features).

# Returns

  * `Float64`: The log-likelihood of the data given the model.
