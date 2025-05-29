```
RefStorage(
    id,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input::Dict{<:Resource,<:Real},
    output::Dict{<:Resource,<:Real},
    data::Vector,
)
```

Legacy constructor for a `RefStorage{ResourceCarrier}`. This version will be discontinued in the near future and replaced with the new version of `RefStorage{StorageBehavior}` in which the parametric input defines the behaviour of the storage.

See the *[documentation](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/how-to/update-models)* for further information regarding how you can translate your existing model to the new model.
