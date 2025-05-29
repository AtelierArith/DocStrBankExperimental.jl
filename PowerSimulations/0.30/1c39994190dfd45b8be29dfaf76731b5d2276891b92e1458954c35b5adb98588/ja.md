```julia
get_all_constraint_index(
    model::PowerSimulations.OperationModel
) -> Vector{Tuple{InfrastructureSystems.Optimization.ConstraintKey, Int64, Int64}}

```

各タプルは (con*name, internal*index, moi_index) に対応します。
