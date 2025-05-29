```
solve(gprob::GreekProblem{PricingProblem{VanillaOption{TS,TE,European,B,C},I}, L}, ::AnalyticGreek, ::BlackScholesAnalytic) where {TS,TE,B,C,L, I<:BlackScholesInputs}
```

Solve a first-order Greek problem for European vanilla options using closed-form Black-Scholes formulas.

# Arguments

  * `gprob`: The Greek problem to solve.
  * `::AnalyticGreek`: The method to use (analytic formulas).
  * `::BlackScholesAnalytic`: The pricing method (Black-Scholes analytic).

# Returns

  * A `GreekResult` containing the calculated Greek.
