```
AbstractInvestmentModel <: EnergyModel
```

An abstract investment model type.

This abstract model type should be used when creating additional [`EnergyModel`](@ref) types that should utilize investments.

!!! note
    Although it is declared within `EnergyModelsBase`, its concrete is only accessible if `EnergyModelsInvestments` is loaded


An example for additional types is given by the inclusion of, *e.g.*, `SDDP`.
