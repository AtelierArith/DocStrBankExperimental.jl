```julia
struct TuningNUTS{M, D}
```

Tune the step size `ϵ` during sampling, and the metric of the kinetic energy at the end of the block. The method for the latter is determined by the type parameter `M`, which can be

1. `Diagonal` for diagonal metric (the default),
2. `Symmetric` for a dense metric,
3. `Nothing` for an unchanged metric.

# Results

A `NamedTuple` with the following fields:

  * `posterior_matrix`, a matrix of position vectors, indexes by `[parameter_index, draw_index]`
  * `tree_statistics`, a vector of tree statistics for each sample
  * `ϵs`, a vector of step sizes for each sample

# Fields

  * `N`: Number of samples.
  * `stepsize_adaptation`: Dual averaging parameters.
  * `λ`: Regularization factor for normalizing variance. An estimated covariance matrix `Σ` is rescaled by `λ` towards $σ²I$, where $σ²$ is the median of the diagonal. The constructor has a reasonable default.
