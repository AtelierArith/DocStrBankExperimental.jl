```
solve(gprob::SecondOrderGreekProblem, method::FiniteDifference, pricing_method::P) where {P<:AbstractPricingMethod}
```

Solve a second-order Greek problem using finite differences.

# Arguments

  * `gprob`: The second-order Greek problem to solve.
  * `method`: Finite difference method configuration.
  * `pricing_method`: The method to use for pricing.

# Returns

  * A `GreekResult` containing the calculated second-order Greek.
