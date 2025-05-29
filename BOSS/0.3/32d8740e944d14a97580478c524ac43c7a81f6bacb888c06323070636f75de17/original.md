```
SampleOptAM(; kwargs...)
```

Optimizes the acquisition function by first sampling candidates from the user-provided prior, and then running multiple optimization runs initiated from the samples with the highest acquisition values.

# Keywords

  * `x_prior::MultivariateDistribution`: The prior over the input domain used to sample candidates.
  * `samples::Int`: The number of samples to be drawn and evaluated.
  * `algorithm::Any`: Defines the optimization algorithm.
  * `multistart::Int`: The number of optimization restarts.
  * `parallel::Bool`: If `parallel=true`, both the sampling and individual optimization runs       are performed in parallel.
  * `autodiff:SciMLBase.AbstractADType:`: The automatic differentiation module       passed to `Optimization.OptimizationFunction`.
  * `kwargs...`: Other kwargs are passed to the optimization algorithm.
