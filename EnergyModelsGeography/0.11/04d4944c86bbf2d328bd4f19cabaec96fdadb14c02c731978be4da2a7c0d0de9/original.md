```
PipeLinepackSimple(
    id::String,
    inlet::EMB.Resource,
    outlet::EMB.Resource,
    consuming::EMB.Resource,
    consumption_rate::TimeProfile,
    trans_cap::TimeProfile,
    trans_loss::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    energy_share::Float64,
    directions::Int = 1
    data::Vector{Data} = Data[]
)
```

Legacy constructor for a `PipeLinepackSimple`. This version will be discontinued in the near future and replaced with the new version that is no longer using the field directions.

See the *[documentation](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/how-to/update-models)* for further information regarding how you can translate your existing model to the new model.
