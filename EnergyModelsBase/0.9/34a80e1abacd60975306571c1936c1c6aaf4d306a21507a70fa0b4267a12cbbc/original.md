```
InvData(;
    capex_cap::TimeProfile,
    cap_max_inst::TimeProfile,
    cap_max_add::TimeProfile,
    cap_min_add::TimeProfile,
    inv_mode::Investment = ContinuousInvestment(),
    cap_start::Union{Real, Nothing} = nothing,
    cap_increment::TimeProfile = FixedProfile(0),
    life_mode::LifetimeMode = UnlimitedLife(),
    lifetime::TimeProfile = FixedProfile(0),
)
```

Legacy constructor for a `InvData`.

The new storage descriptions allows now for a reduction in functions which is used to make `EnergModelsInvestments` less dependent on `EnergyModelsBase`.

The core changes to the existing structure is the move of the required parameters to the type `Investment` (*e.g.*, the minimum and maximum added capacity is only required for investment modes that require these parameters) as well as moving the `lifetime` to the type `LifetimeMode`, when required.

See the *[documentation](https://energymodelsx.github.io/EnergyModelsInvestments.jl/how-to/update-models)* for further information regarding how you can translate your existing model to the new model.

!!! note
    Although it is declared within `EnergyModelsBase`, its concrete is only accessible if `EnergyModelsInvestments` is loaded

