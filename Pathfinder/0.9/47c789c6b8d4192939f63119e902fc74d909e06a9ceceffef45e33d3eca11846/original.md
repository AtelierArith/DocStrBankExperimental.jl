```
MultiPathfinderResult
```

Container for results of multi-path Pathfinder.

# Fields

  * `input`: User-provided input object, e.g. either `logp`, `(logp, ∇logp)`, `optim_fun`,   `optim_prob`, or another object.
  * `optimizer`: Optimizer used for maximizing the log-density
  * `rng`: Pseudorandom number generator that was used for sampling
  * `optim_prob::`[`SciMLBase.OptimizationProblem`](@extref): Otimization problem used for   optimization
  * `logp`: Log-density function
  * `fit_distribution::`[`Distributions.MixtureModel`](@extref): uniformly-weighted mixture of   ELBO-maximizing multivariate normal distributions from each run.
  * `draws::AbstractMatrix{<:Real}`: draws from `fit_distribution` with size `(dim, ndraws)`,   potentially resampled using importance resampling to be closer to the target   distribution.
  * `draw_component_ids::Vector{Int}`: component id of each draw in `draws`.
  * `fit_distribution_transformed`: `fit_distribution` transformed to the same space as the   user-supplied target distribution. This is only different from `fit_distribution` when   integrating with other packages, and its type depends on the type of `input`.
  * `draws_transformed`: `draws` transformed to be draws from `fit_distribution_transformed`.
  * `pathfinder_results::Vector{<:`[`PathfinderResult`](@ref)`}`: results of each single-path   Pathfinder run.
  * `psis_result::Union{Nothing,<:`[`PSIS.PSISResult`](@extref)`}`: If importance resampling   was used, the result of Pareto-smoothed importance resampling.   `psis_result.pareto_shape` also diagnoses whether `draws` can be used to compute   estimates from the target distribution.
