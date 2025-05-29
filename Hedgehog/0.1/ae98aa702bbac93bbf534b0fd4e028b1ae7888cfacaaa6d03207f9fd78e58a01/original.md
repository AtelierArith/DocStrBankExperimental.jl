```
solve(gprob::SecondOrderGreekProblem, ::ForwardAD, pricing_method::P) where {P<:AbstractPricingMethod}
```

Solve a second-order Greek problem using automatic differentiation.

# Arguments

  * `gprob`: The second-order Greek problem to solve.
  * `::ForwardAD`: The method to use (automatic differentiation).
  * `pricing_method`: The method to use for pricing.

# Returns

  * A `GreekResult` containing the calculated second-order Greek.
