```
abcdesmc!(prior, dist!, ϵ_target, varexternal; <keyword arguments>)
```

Run ABC with diffential evolution (de) moves in a Sequential Monte Carlo setup (smc)  providing posterior samples and a model evidence estimate.

The particles have to be weighted (via `r.Wns`) for valid posterior samples.

# Arguments

  * `prior`: `Distribution` or `Factored` object specifying the parameter prior.
  * `dist!`: distance function computing the distance (`≥ 0.0`) between model and data,    for given `(θ, ve)` input (`θ` parameters, `ve` external variables, see `varexternal`).
  * `ϵ_target`: final target distance (or more general, target width of the ABC kernel); algorithm    stops if `ϵ_target` or `nsims_max` is reached.
  * `varexternal`: external variables that are passed as second positional argument to `dist!`    and can be used to support the distance computation with fast in-place operations in    a thread-safe manner; objects in `varexternal` can be in-place mutated, even in `parallel` mode,    as each thread will receive its own copy of `varexternal` (if not needed input `nothing`).
  * `nparticles::Int=100`: number of total particles to use for inference.
  * `α=0.95`: used for adaptive choice of ϵ specifying the sequential target distributions; technically,    ϵ will be the `α`-quantile of current particle distances.
  * `δess=0.5`: if the fractional effective sample size drops below `δess`, a stratified resampling step is performed.
  * `nsims_max::Int=10^7`: maximal number of `dist!` evaluations (not counting initial samples from prior);    algorithm stops if `ϵ_target` or `nsims_max` is reached.
  * `Kmcmc::Int=3`: number of MCMC (Markov chain Monte Carlo) steps at each sequential    target distribution specified by current ϵ and ABC kernel type; actual number can be    lower due to early exits as specified by `Kmcmc_min`.
  * `Kmcmc_min=1.0`: minimal value for accumulated acceptances per alive particle; if this value    is reached earlier (before completing the total `Kmcmc` MCMC steps) the loop is early-exited;    set `Kmcmc_min=Inf` to compute exactly `Kmcmc` MCMC steps at each ϵ target.
  * `ABCk=ABCdeZ.Indicator0toϵ`: ABC kernel to be specified by ϵ widths that receives distance values.
  * `facc_min=0.15`: if the fraction of accepted MCMC proposals drops below `facc_min`, diffential evolution    proposals are reduced by a factor of `facc_tune`.
  * `facc_tune=0.975`: factor to reduce the jump distance of the diffential evolution    proposals in the MCMC step (used if `facc_min` is reached).
  * `verbose::Bool=true`: if set to `true`, enables verbosity (printout to REPL).
  * `verboseout::Bool=true`: if set to `true`, algorithm returns a more detailed inference output.
  * `rng=Random.GLOBAL_RNG`: an AbstractRNG object which is used by the inference.
  * `parallel::Bool=false`: if set to `true`, threaded parallelism is enabled; `dist!` must be    thread-safe in such a case, e.g. by making use of `varexternal` (`ve`).

# Examples

```julia-repl
julia> using ABCdeZ, Distributions;
julia> data = 5;
julia> prior = Normal(0, sqrt(10));
julia> model(θ) = rand(Normal(θ, 1));
julia> dist!(θ, ve) = abs(model(θ)-data), nothing;
julia> ϵ = 0.3;
julia> r = abcdesmc!(prior, dist!, ϵ, nothing, nparticles=1000, parallel=true);
julia> posterior = [t[1] for t in r.P[r.Wns .> 0.0]];
julia> evidence = exp(r.logZ);
```
