```
mcmctest([rng,] test, subject; kwargs...)
```

Sample a p-value according to `test` for `subject`

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator. (Default: `Random.default_rng()`.)
  * `test::AbstractMCMCTest`: Test strategy.
  * `subject::TestSubject`: MCMC algorithm and model subject to test.

# Keyword Arguments

  * `show_progress::Bool`: Whether to show the progress bar. (Default: `true`.)
  * `statistics`: Function for computing test statistics from samples generated from the tests. (See section below for additional description.)
  * Check the documentation for the respective test strategy for additional keyword arugments.

# Custom Test Statistics

The statistics used for the hypothesis tests can be modified by passing a custom funciton to `statistics`. The default statistics are the first and second moments computed as below.

```julia
statistics = params -> vcat(params, params.^2)
```

The cross-interaction can also be tested by adding an additional entry as below.

```julia
statistics = params -> vcat(params, params.^2, reshape(params*params',:))
```

But naturally, adding more statistics increase the computational cost of computing the tests.

Also, different tests may result in different statistics being computed through the same `statistics` function. For example, the two-sample test strategies generate both model parameters `θ` and data `y`. Therefore, `params = vcat(θ, y)`. On the other hand, the exac rank test only generates model parameters `θ`. Therefore, `params = θ`. Naturally, `statistics` can also be used to `select` a subset of parameters used for testing. For example, for the two-sample test strategies, if we only want to use `θ` for the tests, where `d = length(θ) > 0`, one can do the following:

```julia
statistics = params -> θ[1:d]
```
