```
SingleInvData <: InvestmentData
```

Extra investment data for type investments. The extra investment data has only a single field in which `AbstractInvData` has to be added.

The advantage of separating `AbstractInvData` from the `InvestmentData` node is to allow easier separation of `EnergyModelsInvestments` and `EnergyModelsBase` and provides the user with the potential of introducing new capacities for types.

# Fields

  * **`cap::AbstractInvData`** is the investment data for the capacity.

When multiple inputs are provided, a constructor directly creates the corresponding `AbstractInvData`.

# Fields

  * **`capex::TimeProfile`** is the capital costs for investing in a capacity. The value is relative to the added capacity.
  * **`max_inst::TimeProfile`** is the maximum installed capacity in a strategic period.
  * **`initial::Real`** is the initial capacity. This results in the creation of a [`StartInvData`](@extref EnergyModelsInvestments.StartInvData) type for the investment data.
  * **`inv_mode::Investment`** is the chosen investment mode for the technology. The following investment modes are currently available: [`BinaryInvestment`](@extref EnergyModelsInvestments), [`DiscreteInvestment`](@extref EnergyModelsInvestments), [`ContinuousInvestment`](@extref EnergyModelsInvestments), [`SemiContinuousInvestment`](@extref EnergyModelsInvestments), or [`FixedInvestment`](@extref EnergyModelsInvestments).
  * **`life_mode::LifetimeMode`** is type of handling the lifetime. Several different alternatives can be used: [`UnlimitedLife`](@extref EnergyModelsInvestments), [`StudyLife`](@extref EnergyModelsInvestments), [`PeriodLife`](@extref EnergyModelsInvestments), or [`RollingLife`](@extref EnergyModelsInvestments). If `life_mode` is not specified, the model assumes an [`UnlimitedLife`](@extref EnergyModelsInvestments).
