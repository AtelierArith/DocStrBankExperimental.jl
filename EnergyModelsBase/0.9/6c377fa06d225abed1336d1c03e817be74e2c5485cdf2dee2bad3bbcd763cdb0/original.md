```
OperationalModel <: EnergyModel
```

Operational Energy Model without investments.

# Fields

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** is a dictionary with individual emission limits as `TimeProfile` for each emission resource [`ResourceEmit`](@ref).
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** are the emission costs for each emission resources [`ResourceEmit`](@ref).
  * **`co2_instance`** is a [`ResourceEmit`](@ref) and corresponds to the type used for CO₂.
