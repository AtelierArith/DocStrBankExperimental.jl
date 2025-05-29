```
sample(model::DEModel, de::DE, n_iter::Int; progress=false, kwargs...)
```

Samples from the posterior distribution.

# Arguments

  * `model`: a model containing likelihood function with data and priors
  * `de`: differential evolution object
  * `n_iter`: number of iterations or samples

# Keywords

  * `progress=false`: show progress of sampler
  * `kwargs...`: optional keyword arguments
