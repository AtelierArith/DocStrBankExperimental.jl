```
InvestmentModel <: AbstractInvestmentModel
```

A concrete basic investment model type based on the standard [`OperationalModel`](@ref). The concrete basic investment model is similar to an `OperationalModel`, but allows for investments and additional discounting of future years.

!!! note
    Although it is declared within `EnergyModelsBase`, its concrete is only accessible if `EnergyModelsInvestments` is loaded


# Fields

  * **`emission_limit::Dict{<:ResourceEmit, <:TimeProfile}`** is a dictionary with individual emission limits as `TimeProfile` for each emission resource [`ResourceEmit`](@ref).
  * **`emission_price::Dict{<:ResourceEmit, <:TimeProfile}`** are the emission costs for each emission resources [`ResourceEmit`](@ref).
  * **`co2_instance`** is a [`ResourceEmit`](@ref) and corresponds to the type used for CO₂.
  * **`r::Float64`** is the discount rate in the investment optimization.
