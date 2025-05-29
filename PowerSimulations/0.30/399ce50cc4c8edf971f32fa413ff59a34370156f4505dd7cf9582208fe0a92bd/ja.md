```julia
get_all_variable_index(
    model::PowerSimulations.OperationModel
) -> Vector{Tuple{Symbol, Int64, Int64}}

```

各タプルは (con*name, internal*index, moi_index) に対応します。
