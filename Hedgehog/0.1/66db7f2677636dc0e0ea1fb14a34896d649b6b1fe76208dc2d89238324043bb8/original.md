```
BlackScholesInputs <: AbstractMarketInputs
```

Market data inputs for the Black-Scholes model.

# Fields

  * `referenceDate`: The date from which maturity is measured.
  * `rate`: The risk-free interest rate (annualized).
  * `spot`: The current spot price of the underlying asset.
  * `sigma`: The volatility of the underlying asset (annualized).

This struct encapsulates the necessary inputs for pricing derivatives under the Black-Scholes model.
