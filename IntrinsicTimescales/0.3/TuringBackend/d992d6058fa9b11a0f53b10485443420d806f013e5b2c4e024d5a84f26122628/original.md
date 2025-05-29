```
get_param_dict_advi()
```

Get default parameter dictionary for ADVI (Automatic Differentiation Variational Inference) algorithm.

# Returns

Dictionary containing default values for ADVI parameters including:

  * `n_samples`: Number of posterior samples to draw (default: 4000)
  * `n_iterations`: Number of ADVI iterations (default: 50)
  * `n_elbo_samples`: Number of samples for ELBO estimation (default: 20)
  * `autodiff`: Automatic differentiation backend (default: AutoForwardDiff())
