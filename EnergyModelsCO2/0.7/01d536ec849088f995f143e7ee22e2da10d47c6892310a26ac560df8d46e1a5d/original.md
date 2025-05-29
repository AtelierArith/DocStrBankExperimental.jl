```
CO2Storage(
    id,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input::Dict{<:Resource,<:Real},
    output::Dict{<:Resource,<:Real},
    data::Array{<:Data},
)
```

Legacy constructor for a `CO2Storage`. This version will be discontinued in the near future and replaced with the new version of `CO2Storage` in which the parametric input (not included due to inner constructor) defines the behaviour of the storage. In addition, the new version supports variable and fixed operating expenses for both the charge capacity and the level.
