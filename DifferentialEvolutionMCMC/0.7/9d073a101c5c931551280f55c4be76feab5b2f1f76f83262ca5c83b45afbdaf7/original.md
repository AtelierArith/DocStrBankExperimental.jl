```
sample(model::DEModel, de::DE, ::MCMCThreads, n_iter::Int; progress=false, kwargs...)
```

Samples from the posterior distribution with each group of particles on a seperarate thread for the mutation and crossover steps.

# Arguments

  * `model`: a model containing likelihood function with data and priors
  * `de`: differential evolution object
  * `MCMCThreads`: pass MCMCThreads() object to run on multiple threads
  * `n_iter`: number of iterations or samples

# Keywords

  * `progress=false`: show progress of sampler
  * `kwargs...`: optional keyword arguments
