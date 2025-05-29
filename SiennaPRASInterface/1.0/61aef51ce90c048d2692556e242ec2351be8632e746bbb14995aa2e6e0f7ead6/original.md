```julia
generate_pras_system(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}
generate_pras_system(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    export_location::Union{Nothing, String}
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}

```

Use a RATemplate to create a PRAS system from a Sienna system.

# Arguments

  * `sys::PSY.System`: Sienna PowerSystems System
  * `template::RATemplate`: RATemplate
  * `export_location::Union{Nothing, String}`: Export location for PRAS SystemModel

# Returns

  * `PRASCore.SystemModel`: PRAS SystemModel

# Examples

```julia
generate_pras_system(sys, template)
```

Note that the original system will only be set to NATURAL_UNITS.
