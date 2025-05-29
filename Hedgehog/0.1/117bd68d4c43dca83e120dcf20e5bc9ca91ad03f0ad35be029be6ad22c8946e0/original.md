A `PricingProblem` bundles the payoff and the market inputs required to price a derivative.

# Type Parameters

  * `P<:AbstractPayoff`: The payoff type (e.g., VanillaOption).
  * `M<:AbstractMarketInputs`: The market data type (e.g., volatility surface, interest rate curve).

# Fields

  * `payoff::P`: The payoff object describing the contract to be priced.
  * `market::M`: The market data needed for pricing.
