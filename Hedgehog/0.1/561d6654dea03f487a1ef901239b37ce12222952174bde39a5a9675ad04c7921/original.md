```
solve(prob::PricingProblem{VanillaOption{European}}, ::BlackScholesAnalytic) -> AnalyticSolution
```

Computes the price of a European vanilla option under the Black-Scholes model.

# Arguments

  * `prob::PricingProblem`: The pricing problem, including the payoff and market inputs.
  * `BlackScholesAnalytic`: Marker for the analytic pricing method.

# Returns

  * `AnalyticSolution`: The priced solution under Black-Scholes assumptions.

# Notes

  * Uses the forward measure formulation.
  * Falls back to intrinsic value if volatility is zero.
