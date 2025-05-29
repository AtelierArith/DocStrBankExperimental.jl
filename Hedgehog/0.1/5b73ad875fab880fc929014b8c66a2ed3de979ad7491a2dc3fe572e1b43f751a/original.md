```
solve(gprob::SecondOrderGreekProblem, ::AnalyticGreek, ::BlackScholesAnalytic)
```

Solve a second-order Greek problem using closed-form Black-Scholes formulas.

# Arguments

  * `gprob`: The second-order Greek problem to solve.
  * `::AnalyticGreek`: The method to use (analytic formulas).
  * `::BlackScholesAnalytic`: The pricing method (Black-Scholes analytic).

# Returns

  * A `GreekResult` containing the calculated second-order Greek.
