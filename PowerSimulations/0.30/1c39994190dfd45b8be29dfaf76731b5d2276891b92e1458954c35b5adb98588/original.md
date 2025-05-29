```julia
get_all_constraint_index(
    model::PowerSimulations.OperationModel
) -> Vector{Tuple{InfrastructureSystems.Optimization.ConstraintKey, Int64, Int64}}

```

Each Tuple corresponds to (con*name, internal*index, moi_index)
