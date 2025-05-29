```
struct RecHorOperationalModel <: RecHorEnergyModel
```

Operational energy model without investments, receding horizon implementation.

# Fields

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** is a dictionary with individual emission limits as `TimeProfile` for each emission resource `ResourceEmit`.
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** are the prices for the different emissions types considered.
  * **`co2_instance`** is a `ResourceEmit` and corresponds to the type used for CO₂.
