```
solve(prob::PricingProblem, method::LSM)
```

Prices an American option using the Least Squares Monte Carlo method.

# Arguments

  * `prob`: A `PricingProblem` containing an American `VanillaOption`.
  * `method`: An `LSM` pricing method.

# Returns

  * An `LSMSolution` containing price and stopping strategy.
