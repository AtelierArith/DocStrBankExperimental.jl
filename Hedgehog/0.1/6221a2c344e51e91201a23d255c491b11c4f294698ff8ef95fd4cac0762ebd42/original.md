```
solve(gprob::BatchGreekProblem{P,L}, method::GreekMethod, pricing_method::AbstractPricingMethod) where {P,L}
```

Solve multiple Greek problems simultaneously.

# Arguments

  * `gprob`: The batch Greek problem to solve.
  * `method`: The method to use for Greek calculation.
  * `pricing_method`: The method to use for pricing.

# Returns

  * A dictionary mapping lenses to their corresponding Greeks.
