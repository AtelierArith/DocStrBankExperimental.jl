```
HestonInputs <: AbstractMarketInputs
```

Market data inputs for the Heston stochastic volatility model.

# Fields

  * `referenceDate`: The base date for maturity calculation (in ticks).
  * `rate`: The risk-free interest rate (annualized).
  * `spot`: The current spot price of the underlying.
  * `V0`: The initial variance of the underlying.
  * `κ`: The rate at which variance reverts to its long-term mean.
  * `θ`: The long-term mean of the variance.
  * `σ`: The volatility of variance (vol-of-vol).
  * `ρ`: The correlation between the asset and variance processes.

Used for pricing under the Heston model and simulation of stochastic volatility paths.
