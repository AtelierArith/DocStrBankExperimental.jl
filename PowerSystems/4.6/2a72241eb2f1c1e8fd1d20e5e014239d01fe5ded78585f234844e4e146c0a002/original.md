```julia
PowerModelsData(
    file::Union{IO, String};
    kwargs...
) -> PowerSystems.PowerModelsData

```

Constructs PowerModelsData from a raw file. Currently Supports MATPOWER and PSSE data files parsed by PowerModels.
