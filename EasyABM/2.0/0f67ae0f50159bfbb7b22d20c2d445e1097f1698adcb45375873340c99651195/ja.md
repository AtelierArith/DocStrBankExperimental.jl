```julia
get_edge_data(
    edge,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}}
) -> @NamedTuple{birth_death_times::Vector{Tuple{Int64, Int64}}, record::DataFrames.DataFrame}
get_edge_data(
    edge,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}},
    props
) -> @NamedTuple{birth_death_times::Vector{Tuple{Int64, Int64}}, record::DataFrames.DataFrame}

```
