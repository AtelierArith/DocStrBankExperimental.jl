```
TwoSampleTest(n_samples, n_mcmc_steps; n_control, n_treatment, n_mcmc_thin)
```

Two-sample hypothesis testing strategy. Algorithm 1 in Gandy & Scott (2021).

# Arguments

  * `n_samples::Int`: Number of samples from the joint `p(θ, y)` used for the computing the p-values.
  * `n_mcmc_steps::Int`: Number of times the MCMC kernel is applied to initial sample from the joint. (Increasing this value improves the power of the test.)

# Keyword Arguments

  * `n_control::Int`: Number of pure samples from the joint (control group). (Default: `n_samples`)
  * `n_treatment::Int`: Number of samples from the MCMC kernel (treatment group). (Default: `n_samples`)
  * `n_mcmc_thin::Int`: Number of thinning applied to the MCMC chain. The effect of this argument is the same as `n_mcmc_steps`.

# Returns

  * `pvalues`: P-value computed for each dimension of the statistic returned from `statistics`.

# Requirements

This test requires the following functions for `model` and `kernel` to be implemented:

  * `markovchain_transition`
  * `sample_joint`

# Keyword Arguments for Tests

When calling `mcmctest` or `seqmcmctest`, this tests has an additional keyword argument:

  * `two_sample_test_pvalue`: The p-value calculation strategy.

The default strategy is an approximate two-sample Kolmogorov-Smirnov test. Any function returning a single p-value from a two-sample hypothesis test will work. The format is as follows:

```julia
two_sample_test_pvalue(x::AbstractVector, y::AbstractVector)::Real
```
