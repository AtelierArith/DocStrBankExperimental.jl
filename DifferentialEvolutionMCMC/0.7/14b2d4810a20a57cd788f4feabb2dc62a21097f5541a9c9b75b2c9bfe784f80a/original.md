```
optimize(model::DEModel, de::DE, ::MCMCThreads, n_iter::Int; progress=false, kwargs...)
```

Finds optimal set of parameters.

# Arguments

  * `model`: a model containing likelihood function with data and priors
  * `de`: differential evolution object
  * `MCMCThreads`: pass MCMCThreads() object to run on multiple threads
  * `n_iter`: number of iterations or samples

# Keywords

  * `progress=false`: show progress of algorithm
  * `kwargs...`: optional keyword arguments
