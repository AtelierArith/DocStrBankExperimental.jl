```
ExactRankTest(n_samples, n_mcmc_steps; n_mcmc_thin)
```

Exact rank hypothesis testing strategy for reversible MCMC kernels. Algorithm 2 in Gandy & Scott (2021).

# Arguments

  * `n_samples::Int`: Number of ranks to be simulated.
  * `n_mcmc_steps::Int`: Number of MCMC states to be simulated for simulating a single rank.
  * `n_mcmc_thin::Int`: Number of thinning applied to the MCMC chain.

# Returns

  * `pvalues`: P-value computed for each dimension of the statistic returned from `statistics`.

# Requirements

This test requires the following functions for `model` and `kernel` to be implemented:

  * `markovchain_transition`
  * `sample_joint`

Furthermore, this test explicitly assumes the following

  * `kernel` is reversible.

For reference, the following kernels are reversible:

  * Any Metropolis-Hastings kernel
  * slice samplers
  * Hamiltonian Monte Carlo/No-U-Turn Samplers with resampling over the trajectory
  * random-scan/permutation-scan Gibbs samplers
  * Unadjusted Langevin

However, the following kernels are not reversible:

  * Hamiltonian Monte Carlo with persistent momentum (a.k.a Horowitz's method, generalized Hamiltonian Monte Carlo)
  * Systematic-scan Gibbs samplers
  * Piecewise deterministic Markov processes

!!! info
    Applying this test to an irreversible `kernel` will result in false negatives even if its stationary distribution is correct.


# Keyword Arguments for Tests

When calling `mcmctest` or `seqmcmctest`, this tests has an additional keyword argument:

  * `uniformity_test_pvalue`: The p-value calculation strategy.

The default strategy is an $\chi^2$ test. Any function returning a single p-value from a uniformity hypothesis test will work. The format is as follows:

```julia
uniformity_test_pvalue(x::AbstractVector)::Real
```
