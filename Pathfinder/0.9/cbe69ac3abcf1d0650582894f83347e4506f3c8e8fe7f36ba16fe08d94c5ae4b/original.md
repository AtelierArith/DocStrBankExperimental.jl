```
multipathfinder(fun, ndraws; kwargs...)
```

Run [`pathfinder`](@ref) multiple times to fit a multivariate normal mixture model.

For `nruns=length(init)`, `nruns` parallel runs of pathfinder produce `nruns` multivariate normal approximations $q_k = q(\phi | \mu_k, \Sigma_k)$ of the posterior. These are combined to a mixture model $q$ with uniform weights.

$q$ is augmented with the component index to generate random samples, that is, elements $(k, \phi)$ are drawn from the augmented mixture model

$$
\tilde{q}(\phi, k | \mu, \Sigma) = K^{-1} q(\phi | \mu_k, \Sigma_k),
$$

where $k$ is a component index, and $K=$ `nruns`. These draws are then resampled with replacement. Discarding $k$ from the samples would reproduce draws from $q$.

If `importance=true`, then Pareto smoothed importance resampling is used, so that the resulting draws better approximate draws from the target distribution $p$ instead of $q$. This also prints a warning message if the importance weighted draws are unsuitable for approximating expectations with respect to $p$.

# Arguments

  * `fun`: An object representing the log-density of the target distribution. Supported   types include:

      * a callable with the signature   `f(params::AbstractVector{<:Real}) -> log_density::Real`.
      * an object implementing the   [LogDensityProblems interface](@extref LogDensityProblems log-density-api).
      * [`SciMLBase.OptimizationFunction`](@extref): wraps the *negative* log density. It must   have the necessary features (e.g. a gradient or Hessian function) for the chosen   `optimizer`.
      * [`SciMLBase.OptimizationProblem`](@extref): an optimization problem containing a   function with the same properties as the above `OptimizationFunction`, as well as an   initial point. If provided, `init` and `dim` are ignored.
      * [`DynamicPPL.Model`](@extref): a Turing model. If provided, `init` and `dim` are   ignored.
  * `ndraws::Int`: number of approximate draws to return

# Keywords

  * `init`: iterator of length `nruns` of initial points of length `dim` from which each   single-path Pathfinder run will begin. `length(init)` must be implemented. If `init` is   not provided, `nruns` must be, and `dim` must be if `fun` provided.
  * `nruns::Int`: number of runs of Pathfinder to perform. Ignored if `init` is provided.
  * `ndraws_per_run::Int`: The number of draws to take for each component before resampling.   Defaults to a number such that `ndraws_per_run * nruns > ndraws`.
  * `importance::Bool=true`: Perform Pareto smoothed importance resampling of draws.
  * `rng::AbstractRNG=Random.default_rng()`: Pseudorandom number generator. It is recommended to   use a parallelization-friendly PRNG like the default PRNG on Julia 1.7 and up.
  * `executor::Transducers.Executor`: Transducers.jl executor that determines if and how to   run the single-path runs in parallel, defaulting to   [`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`). If a transducer for   multi-threaded computation is selected, you must first verify that `rng` and the log   density function are thread-safe.
  * `executor_per_run::Transducers.Executor`: Transducers.jl executor used within each run to   parallelize PRNG calls, defaulting to   [`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`). See   [`pathfinder`](@ref) for further description.
  * `kwargs...` : Remaining keywords are forwarded to [`pathfinder`](@ref).

# Returns

  * [`MultiPathfinderResult`](@ref)
