```
CalibrationProblem{P, M, A, Accessor, I, Q}
```

Wraps a `BasketPricingProblem` and defines which market parameters should be calibrated using Accessors.jl access paths.

# Fields

  * `pricing_problem::BasketPricingProblem{P, M}`: The basket of payoffs and shared market input.
  * `pricing_method::A`: The pricing method used (e.g., Black-Scholes).
  * `accessors::Vector{Accessor}`: List of `Accessors.jl` lenses specifying which parameters to calibrate.
  * `quotes::Vector{Q}`: Observed market prices to match.
  * `initial_guess::Vector{I}`: Initial guesses for each calibrated parameter.
