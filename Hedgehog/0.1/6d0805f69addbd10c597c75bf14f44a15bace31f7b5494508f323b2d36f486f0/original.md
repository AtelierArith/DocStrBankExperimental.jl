```
BasketPricingProblem(payoffs, market_inputs)
```

Container for pricing several payoffs under a single market scenario.

# Fields

  * `payoffs::Vector{P}`       — collection of payoffs to be priced.
  * `market_inputs::M`         — market data (yield curves, vols, etc.) shared by all payoffs.
