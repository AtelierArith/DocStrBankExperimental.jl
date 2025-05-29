```julia
get_agent_data(
    agent::EasyABM.AbstractAgent,
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.MortalType}, EasyABM.AbstractSpaceModel{EasyABM.MortalType}}
) -> @NamedTuple{birthtime::Int64, deathtime::Int64, record::DataFrames.DataFrame}
get_agent_data(
    agent::EasyABM.AbstractAgent,
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.MortalType}, EasyABM.AbstractSpaceModel{EasyABM.MortalType}},
    props
) -> @NamedTuple{birthtime::Int64, deathtime::Int64, record::DataFrames.DataFrame}

```
