```julia
get_agent_data(
    agent::EasyABM.AbstractAgent,
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.StaticType}, EasyABM.AbstractSpaceModel{EasyABM.StaticType}}
) -> @NamedTuple{record::DataFrames.DataFrame}
get_agent_data(
    agent::EasyABM.AbstractAgent,
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.StaticType}, EasyABM.AbstractSpaceModel{EasyABM.StaticType}},
    props
) -> @NamedTuple{record::DataFrames.DataFrame}

```
