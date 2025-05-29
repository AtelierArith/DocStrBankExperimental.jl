```
solve(gprob::GreekProblem, ::ForwardAD, pricing_method::P) where {P<:AbstractPricingMethod}
```

Solve a first-order Greek problem using automatic differentiation.

# Arguments

  * `gprob`: The Greek problem to solve.
  * `::ForwardAD`: The method to use (automatic differentiation).
  * `pricing_method`: The method to use for pricing.

# Returns

  * A named tuple containing the calculated Greek.
