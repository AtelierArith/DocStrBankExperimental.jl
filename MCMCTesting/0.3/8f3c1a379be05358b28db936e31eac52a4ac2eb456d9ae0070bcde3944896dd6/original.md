```
simulate_ranks([rng,] test, subject; kwargs...)
```

Simulate ranks according to the exact rank test strategy.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator. (Default: `Random.default_rng()`.)
  * `test::AbstractMCMCTest`: Test strategy.
  * `subject::TestSubject`: MCMC algorithm and model subject to test.

# Keyword Arguments

  * `tie_epsilon::Real`: The tolerance for declaring a difference in statistic as a tie. (Default: `eps(Float32)`.)
  * `statistics`: Function for computing test statistics from samples generated from the tests. (See section below for additional description.)
  * `show_progress::Bool`: Whether to show progress.

# Returns

  * ranks::Matrix: The simualted ranks. Each row are the rank samples of each statistic.
