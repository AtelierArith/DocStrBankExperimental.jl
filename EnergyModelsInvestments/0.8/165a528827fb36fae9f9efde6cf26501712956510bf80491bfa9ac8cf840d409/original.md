```
NoStartInvData <: AbstractInvData
```

Investment data in which the initial capacity is not specified in the `AbstractInvData`. Instead, the initial capacity is inferred  from the capacity of the technology through the function [`start_cap(element, t_inv, inv_data::AbstractInvData, cap)`](@ref).

# Fields

  * **`capex::TimeProfile`** is the capital costs for investing in a capacity. The value is relative to the added capacity.
  * **`max_inst::TimeProfile`** is the maximum installed capacity in an investment period.
  * **`inv_mode::Investment`** is the chosen investment mode for the technology. The following investment modes are currently available: [`BinaryInvestment`](@ref), [`DiscreteInvestment`](@ref), [`ContinuousInvestment`](@ref), [`SemiContinuousInvestment`](@ref) or [`FixedInvestment`](@ref).
  * **`life_mode::LifetimeMode`** is type of handling the lifetime. Several different alternatives can be used: [`UnlimitedLife`](@ref), [`StudyLife`](@ref), [`PeriodLife`](@ref) or [`RollingLife`](@ref).
