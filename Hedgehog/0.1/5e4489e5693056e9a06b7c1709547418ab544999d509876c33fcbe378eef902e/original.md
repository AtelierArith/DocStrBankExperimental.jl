```
solve(gprob::GreekProblem, method::FiniteDifference{S,A}, pricing_method::P) where {S<:FDScheme,P<:AbstractPricingMethod,A}
```

Solve a first-order Greek problem using finite differences.

# Arguments

  * `gprob`: The Greek problem to solve.
  * `method`: Finite difference method configuration.
  * `pricing_method`: The method to use for pricing.

# Returns

  * A `GreekResult` containing the calculated Greek.
