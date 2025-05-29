```
log_likelihood(gmm::GaussianMixtureModel, data::Matrix{<:Real})
```

Compute the log-likelihood of the data given the Gaussian Mixture Model (GMM). The data matrix should be of shape (# observations, # features).

# Returns

  * `Float64`: The log-likelihood of the data given the model.
