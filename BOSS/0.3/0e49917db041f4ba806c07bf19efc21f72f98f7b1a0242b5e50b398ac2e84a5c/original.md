```
SamplingAM(; kwargs...)
```

Optimizes the acquisition function by sampling candidates from the user-provided prior, and returning the sample with the highest acquisition value.

# Keywords

  * `x_prior::MultivariateDistribution`: The prior over the input domain used to sample candidates.
  * `samples::Int`: The number of samples to be drawn and evaluated.
  * `parallel::Bool`: If `parallel=true` then the sampling is parallelized. Defaults to `true`.
