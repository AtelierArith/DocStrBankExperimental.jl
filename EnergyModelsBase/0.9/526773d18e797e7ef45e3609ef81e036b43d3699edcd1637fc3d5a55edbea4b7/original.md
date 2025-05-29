```
InvDataStorage(;
    #Investment data related to storage power
    capex_rate::TimeProfile,
    rate_max_inst::TimeProfile,
    rate_max_add::TimeProfile,
    rate_min_add::TimeProfile,
    capex_stor::TimeProfile,
    stor_max_inst::TimeProfile,
    stor_max_add::TimeProfile,
    stor_min_add::TimeProfile,
    inv_mode::Investment = ContinuousInvestment(),
    rate_start::Union{Real, Nothing} = nothing,
    stor_start::Union{Real, Nothing} = nothing,
    rate_increment::TimeProfile = FixedProfile(0),
    stor_increment::TimeProfile = FixedProfile(0),
    life_mode::LifetimeMode = UnlimitedLife(),
    lifetime::TimeProfile = FixedProfile(0),
)
```

Storage descriptions were changed in EnergyModelsBase v0.7 resulting in the requirement for rewriting the investment options for `Storage` nodes.

See the *[documentation](https://energymodelsx.github.io/EnergyModelsInvestments.jl/how-to/update-models)* for further information regarding how you can translate your existing model to the new model.

!!! note
    Although it is declared within `EnergyModelsBase`, its concrete is only accessible if `EnergyModelsInvestments` is loaded

