```julia
get_node_data(
    node::Int64,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}}
) -> @NamedTuple{birthtime::Int64, deathtime::Int64, record::DataFrames.DataFrame}
get_node_data(
    node::Int64,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}},
    props
) -> @NamedTuple{birthtime::Int64, deathtime::Int64, record::DataFrames.DataFrame}

```
