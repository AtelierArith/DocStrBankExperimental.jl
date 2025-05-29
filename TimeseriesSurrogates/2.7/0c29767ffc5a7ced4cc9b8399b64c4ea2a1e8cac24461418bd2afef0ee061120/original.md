```
SurrogateTest(f::Function, x, method::Surrogate; kwargs...) → test
```

Initialize a surrogate test for input data `x`, which can be used in [`pvalue`](@ref). The tests requires as input a function `f` that given a timeseries (like `x`) it outputs a real number, and a method of how to generate surrogates. `f` is the function that computes the discriminatory statistic.

Once called with [`pvalue`](@ref), the `test` estimates and then stores the real value `rval` and surrogate values `vals` of the discriminatory statistic in the fields `rval, vals` respectively. Alternatively, you can use [`fill_surrogate_test!`](@ref) directly if you don't care about the p-value.

`SurrogateTest` automates the process described in the documentation page [Performing surrogate hypothesis tests](@ref).

`SurrogateTest` subtypes `HypothesisTest` and is part of the StatsAPI.jl interface.

## Keywords

  * `rng = Random.default_rng()`: a random number generator.
  * `n::Int = 10_000`: how many surrogates to generate and compute `f` on.
  * `threaded = true`: Whether to parallelize looping over surrogate computations in  to the available threads (`Threads.nthreads()`).
