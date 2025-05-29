```
StochasticIntegrals.get_draws(
    covariance_matrix::CovarianceMatrix{<:Real},
    num::Integer;
    number_generator::NumberGenerator = Mersenne(
        MersenneTwister(1234),
        length(covariance_matrix.labels),
    ),
    antithetic_variates = false,
)
```

get pseudorandom draws from a `CovarianceMatrix` struct. This is basically a convenience wrapper over StochasticIntegrals.get*draws which does the necessary constructing of the structs of that package. If the `antithetic*variates` control is set to true then every second set of draws will be antithetic to the previous. If you want to do something like Sobol sampling you can change the number_generator. See StochasticIntegrals to see what is available (and feel free to make new ones and put in Pull Requests)

### Inputs

  * `covar` - An `CovarianceMatrix` struct that you want to draw from.
  * `num`- The number of draws you want
  * `number_generator`  - A `NumberGenerator` struct that can be queried for a series of unit interval vectors that are then transformed by the covariance matrix into draws.
  * `antithetic_variates` - A boolean indicating if antithetic variates should be used (every second draw is made from 1 - uniformdraw of previous)

### Returns

  * A `Vector` of `Dict`s of draws. Note you can convert this to a dataframe or array with `StochasticIntegrals.to_dataframe` or `StochasticIntegrals.to_array`.
