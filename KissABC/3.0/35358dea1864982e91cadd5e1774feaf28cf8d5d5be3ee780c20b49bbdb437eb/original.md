Adaptive SMC from P. Del Moral 2012, with Affine invariant proposal mechanism, faster that `AIS` for `ABC` targets.

```julia
function smc(
    prior::Distribution,
    cost::Function;
    rng::AbstractRNG = Random.GLOBAL_RNG,
    nparticles::Int = 100,
    M::Int = 1,
    alpha = 0.95,
    mcmc_retrys::Int = 0,
    mcmc_tol = 0.015,
    epstol = 0.0,
    r_epstol = (1 - alpha)^1.5 / 50,
    min_r_ess = alpha^2,
    max_stretch = 2.0,
    verbose::Bool = false,
    parallel::Bool = false,
)
```

  * `prior`: a Distribution object representing the parameters prior.
  * `cost`: a function that given a prior sample returns the cost for said sample (e.g. a distance between simulated data and target data).
  * `rng`: an AbstractRNG object which is used by SMC for inference (it can be useful to make an inference reproducible).
  * `nparticles`: number of total particles to use for inference.
  * `M`: number of cost evaluations per particle, increasing this can reduce the chance of rejecting good particles.
  * `alpha` - used for adaptive tolerance, by solving `ESS(n,ϵ(n)) = α ESS(n-1, ϵ(n-1))` for `ϵ(n)` at step `n`.
  * `mcmc_retrys` - if set > 0, whenever the fraction of accepted particles drops below the tolerance `mcmc_tol` the MCMC step is repeated (no more than `mcmc_retrys` times).
  * `mcmc_tol` - stopping condition for SMC, if the fraction of accepted particles drops below `mcmc_tol` the algorithm terminates.
  * `epstol` - stopping condition for SMC, if the adaptive cost threshold drops below `epstol` the algorithm has converged and thus it terminates.
  * `min_r_ess` - whenever the fractional effective sample size drops below `min_r_ess`, a systematic resampling step is performed.
  * `max_stretch` - the proposal distribution of `smc` is the stretch move of Foreman-Mackey et al. 2013, the larger the parameters the wider becomes the proposal distribution.
  * `verbose` - if set to `true`, enables verbosity.
  * `parallel` - if set to `true`, threaded parallelism is enabled, keep in mind that the cost function must be Thread-safe in such case.

# Example

```Julia
using KissABC
prior=Factored(Normal(0,5), Normal(0,5))
cost((x,y)) = 50*(x+randn()*0.01-y^2)^2+(y-1+randn()*0.01)^2
results = smc(prior, cost, alpha=0.5, nparticles=5000).P
```

output:

```TTY
2-element Array{Particles{Float64,5000},1}:
 1.0 ± 0.029
 0.999 ± 0.012
```
