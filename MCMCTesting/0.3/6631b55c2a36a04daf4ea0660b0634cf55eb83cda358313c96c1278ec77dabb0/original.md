```
seqmcmctest([rng,] test, subject, false_rejection_rate, samplesize; kwargs...)
```

Sequential run multiple hypothesis tests to guarantee `false_rejection_rate`.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator.
  * `test::AbstractMCMCTest`: Test strategy.
  * `subject::TestSubject`: MCMC algorithm and model subject to test.
  * `false_rejection_rate::Real`: Desired false rejection rate.
  * `samplesize::Int`: The number of p-values used at each test iteration.

# Keyword Arguments

  * `samplesize_increase`: Factor of increase for the samplsize after the first test iteration turns out inconclusive. (Default: `2.0`)
  * `show_progress::Bool`: Whether to show progress. (Default: `true`)
  * `pvalue_adjustmeht::MultipleTesting.PValueAdjustment`: P-value adjustment for multiple testing over the elements of the statistic. (Default: `MultipleTesting.Bonferroni()`)

Additional keyword arguments are passed to internal calls to `mcmctest`.

# Returns

  * `test_result::Bool`: `true` if the null-hypothesis (the MCMC algorithm has the correct stationary distribution) wasn't rejected, `false` otherwise.
