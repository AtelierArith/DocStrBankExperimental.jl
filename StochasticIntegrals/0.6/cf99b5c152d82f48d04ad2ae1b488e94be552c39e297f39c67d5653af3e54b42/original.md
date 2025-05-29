```
get_draws(covar::Union{ForwardCovariance,SimpleCovariance}, num::Integer; number_generator::NumberGenerator = Mersenne(MersenneTwister(1234), length(covar.covariance_labels_)), antithetic_variates = false)
```

get pseudorandom draws from a `ForwardCovariance` struct. Other schemes (like quasirandom) can be done by inserting quasirandom numbers in as the uniform*draw. If the `antithetic*variates` control is set to true then every second set of draws will be antithetic to the previous.

### Inputs

  * `covar` - An `ForwardCovariance` or `SimpleCovariance` struct that you want to draw from.
  * `num`- The number of draws you want
  * `number_generator`- How you want to generate random draws.
  * `antithetic_variates` - Do you want antithetic variate sampling.

### Returns

  * A `Vector` of `Dict`s of draws.
