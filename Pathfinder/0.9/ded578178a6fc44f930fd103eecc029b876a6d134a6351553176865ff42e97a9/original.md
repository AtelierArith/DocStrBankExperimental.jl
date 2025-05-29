```
pathfinder(fun; kwargs...)
```

Find the best multivariate normal approximation encountered while maximizing a log density.

From an optimization trajectory, Pathfinder constructs a sequence of (multivariate normal) approximations to the distribution specified by a log density function. The approximation that maximizes the evidence lower bound (ELBO), or equivalently, minimizes the KL divergence between the approximation and the true distribution, is returned.

The covariance of the multivariate normal distribution is an inverse Hessian approximation constructed using at most the previous `history_length` steps.

# Arguments

  * `fun`: An object representing the log-density of the target distribution. Supported   types include:

      * a callable with the signature   `f(params::AbstractVector{<:Real}) -> log_density::Real`.
      * an object implementing the   [LogDensityProblems interface](@extref LogDensityProblems log-density-api).
      * [`SciMLBase.OptimizationFunction`](@extref): wraps the *negative* log density. It must   have the necessary features (e.g. a gradient or Hessian function) for the chosen   `optimizer`.
      * [`SciMLBase.OptimizationProblem`](@extref): an optimization problem containing a   function with the same properties as the above `OptimizationFunction`, as well as an   initial point. If provided, `init` and `dim` are ignored.
      * [`DynamicPPL.Model`](@extref): a Turing model. If provided, `init` and `dim` are   ignored.

# Keywords

  * `dim::Int`: dimension of the target distribution. Ignored if `init` provided.
  * `init::AbstractVector{<:Real}`: initial point of length `dim` from which to begin   optimization. If not provided and `fun` does not contain an initial point, an initial   point of type `Vector{Float64}` and length `dim` is created and filled using   `init_sampler`.
  * `init_scale::Real`: scale factor $s$ such that the default `init_sampler` samples   entries uniformly in the range $[-s, s]$
  * `init_sampler`: function with the signature `(rng, x) -> x` that modifies a vector of   length `dims` in-place to generate an initial point
  * `ndraws_elbo::Int=5`: Number of draws used to estimate the ELBO
  * `ndraws::Int=ndraws_elbo`: number of approximate draws to return
  * `rng::Random.AbstractRNG`: The random number generator to be used for drawing samples
  * `executor::Transducers.Executor`: Transducers.jl executor that   determines if and how to perform ELBO computation in parallel. The default   ([`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`)) performs no   parallelization. If `rng` is known to be thread-safe, and the log-density function is   known to have no internal state, then   [`Transducers.PreferParallel()`](@extref `Transducers.PreferParallel`) may be used to   parallelize log-density evaluation. This is generally only faster for expensive log   density functions.
  * `history_length::Int=6`: Size of the history used to approximate the   inverse Hessian.
  * `optimizer`: Optimizer to be used for constructing trajectory. Can be any optimizer   compatible with [Optimization.jl](https://docs.sciml.ai/Optimization/stable/), so long   as it supports callbacks. Defaults to   [`Optim.LBFGS`](@extref Optim `algo/lbfgs`)`(; m=history_length, linesearch=LineSearches.HagerZhang(), alphaguess=LineSearches.InitialHagerZhang())`.
  * `adtype::`[`ADTypes.AbstractADType`](@extref): Specifies which automatic   differentiation backend should be used to compute the gradient, if `fun` does not   already specify the gradient. Default is   [`ADTypes.AutoForwardDiff()`](@extref `ADTypes.AutoForwardDiff`) See   [Optimization.jl's Automatic Differentiation Recommendations](@extref Optimization ad).
  * `ntries::Int=1_000`: Number of times to try the optimization, restarting if it fails.   Before every restart, a new initial point is drawn using `init_sampler`.
  * `fail_on_nonfinite::Bool=true`: If `true`, optimization fails if the log-density is a   `NaN` or `Inf` or if the gradient is ever non-finite. If `nretries > 0`, then   optimization will be retried after reinitialization.
  * `kwargs...` : Remaining keywords are forwarded to   [`Optimization.solve`](@extref Optimization `CommonSolve.solve`).

# Returns

  * [`PathfinderResult`](@ref)
