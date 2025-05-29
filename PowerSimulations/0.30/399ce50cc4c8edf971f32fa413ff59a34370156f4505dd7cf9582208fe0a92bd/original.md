```julia
get_all_variable_index(
    model::PowerSimulations.OperationModel
) -> Vector{Tuple{Symbol, Int64, Int64}}

```

Each Tuple corresponds to (con*name, internal*index, moi_index)
