```
PathfinderResult
```

Container for results of single-path Pathfinder.

# Fields

  * `input`: User-provided input object, e.g. a LogDensityProblem, `optim_fun`, `optim_prob`,   or another object.
  * `optimizer`: Optimizer used for maximizing the log-density
  * `rng`: Pseudorandom number generator that was used for sampling
  * `optim_prob::`[`SciMLBase.OptimizationProblem`](@extref): Optimization problem used for   optimization
  * `logp`: Log-density function
  * `fit_distribution::`[`Distributions.MvNormal`](@extref): ELBO-maximizing multivariate   normal distribution
  * `draws::AbstractMatrix{<:Real}`: draws from multivariate normal with size `(dim, ndraws)`
  * `fit_distribution_transformed`: `fit_distribution` transformed to the same space as the   user-supplied target distribution. This is only different from `fit_distribution` when   integrating with other packages, and its type depends on the type of `input`.
  * `draws_transformed`: `draws` transformed to be draws from `fit_distribution_transformed`.
  * `fit_iteration::Int`: Iteration at which ELBO estimate was maximized
  * `num_tries::Int`: Number of tries until Pathfinder succeeded
  * `optim_solution::`[`SciMLBase.OptimizationSolution`](@extref): Solution object of   optimization.
  * `optim_trace::Pathfinder.OptimizationTrace`: container for optimization trace of points,   log-density, and gradient. The first point is the initial point.
  * `fit_distributions::AbstractVector{Distributions.MvNormal}`: Multivariate normal   distributions for each point in `optim_trace`, where   `fit_distributions[fit_iteration + 1] == fit_distribution`
  * `elbo_estimates::AbstractVector{<:Pathfinder.ELBOEstimate}`: ELBO estimates for all but   the first distribution in `fit_distributions`.
  * `num_bfgs_updates_rejected::Int`: Number of times a BFGS update to the reconstructed   inverse Hessian was rejected to keep the inverse Hessian positive definite.

# Returns

  * [`PathfinderResult`](@ref)
