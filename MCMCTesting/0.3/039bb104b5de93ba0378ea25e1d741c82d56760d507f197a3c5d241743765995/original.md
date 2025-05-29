```
rankplot(test, ranks; kwargs...)
```

Plot the simulated ranks using `simulate_ranks`. If the test subjects are correct, the ranks should visually resemble samples from a uniform distribution. The black horizontal line shows the density of a uniform distribution, while the colored bands are the 1σ, 2σ, 3σ confidence intervals.

!!! info
    The confidence intervals are derived from the normal approximation of binomials observations and assume uniformly-sized bins.


!!! info
    `Plots` must be imported to use this plot recipe.


# Arguments

  * `test::ExactRankTest`: The exact rank test object used to simulate the ranks.
  * `ranks`: The output of `simulate_rank`.

# Keyword Arguments

  * `stats_names`: The name for the statistics used in the rank simulation. The default argument automatically assign default names. (Default: :auto).
  * Keyword arguments corresponding `Plots` attributes, such as `bins`, `layout`, `size`, may apply.
