```
out = adaptive_rwm(x0, log_p, n; kwargs)
```

Generic adaptive random walk Metropolis algorithm from initial state vector `x0` targetting log probability density `log_p` run for `n` iterations, including adaptive parallel tempering.

# Arguments

  * `x0::Vector{<:AbstractFloat}`: The initial state vector
  * `log_p::Function`: Function that returns log probability density values                    (up to an additive constant) for any state vector.
  * `n::Int`: Total number of iterations

# Keyword arguments

  * `algorithm::Symbol`: The random walk adaptation algorithm; current choices are `:ram` (default), `:am`, `:asm`, `:aswam` and `:rwm`. (Alternatively, if algorithm is a vector of AdaptState, then this will be used as an initial state for adaptation.)
  * `b::Int`: Burn-in length: `b`:th sample is the first saved sample. Default `⌊n/5⌋`
  * `thin::Int`: Thinning factor; only every `thin`:th sample is stored; default `1`
  * `fulladapt::Bool`: Whether to adapt after burn-in; default `true`
  * `Sp`: Saved adaptive state from output to restart MCMC; default `nothing`
  * `Rp`: Saved rng state from output to restart MCMC; default `nothing`
  * `indp::Int`: Index of saved adaptive state to restart MCMC; default `0`
  * `rng::AbstractRNG`: Random number generator; default `Random.GLOBAL_RNG`
  * `q::Function`: Zero-mean symmetric proposal generator (with arguments `x` and `rng`);  default `q=randn!(x, rng)`
  * `L::Int`: Number of parallel tempering levels
  * `acc_sw::AbstractFloat`: Desired acceptance rate between level swaps; default `0.234`
  * `all_levels::Bool`: Whether to store output of all levels; default `false`
  * `log_pr::Function`: Log-prior density function; default `log_pr(x) = 0.0`.
  * `swaps::Symbol`: Swap strategy, one of:  `:single` (default, single randomly picked swap)  `:randperm` (swap in random order)  `:sweep` (up- or downward sweep, picked at random)  `:nonrev` (alternate even/odd sites as in Syed, Bouchard-Côté, Deligiannidis,  Doucet, 	arXiv:1905.02939)
  * `progress::Union{Bool,Progress}`: Whether a progress meter is shown; default `false`

Note that if `log_pr` is supplied, then `log_p(x)` is regarded as the log-likelihood (or, equivalently, log-target is `log_p(x) + log_pr(x)`). Tempering is only applied to `log_p`, not to `log_pr`.

The output `out.X contains the simulated samples (column vectors).`out.allX[k]`for`k>=2` contain higher temperature auxiliary chains (if requested)

# Examples

```
log_p(x) = -.5*sum(x.^2)
o = adaptive_rwm(zeros(2), log_p, 10_000; algorithm=:am)
using MCMCChains, StatsPlots # Assuming MCMCChains & StatsPlots are installed...
c = Chains(o.X[1]', start=o.params.b, thin=o.params.thin); plot(c)
```
