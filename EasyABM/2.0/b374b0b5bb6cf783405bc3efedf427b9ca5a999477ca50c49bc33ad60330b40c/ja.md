```julia
get_node_data(
    node::Int64,
    model::Union{EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}}
) -> @NamedTuple{record::DataFrames.DataFrame}
get_node_data(
    node::Int64,
    model::Union{EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}},
    props
) -> @NamedTuple{record::DataFrames.DataFrame}

```
