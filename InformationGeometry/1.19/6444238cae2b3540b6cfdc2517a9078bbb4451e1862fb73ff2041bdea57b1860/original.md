```
ConditionGrid(DMs::AbstractVector{<:AbstractDataModel}, Trafos::AbstractVector{<:Function}, mle::AbstractVector, LogPriorFn::Union{Nothing,Function}=nothing; Domain::Union{Nothing,Cuboid}=nothing, 
                SkipOptim::Bool=false, pnames::AbstractVector{<:StringOrSymb}=CreateSymbolNames(length(mle)), name::StringOrSymb="")
```

Implements condition grid inspired by R package dMod. Connects different given `DataModel`s via a vector of parameter transformations, which read from the same collective vector of outer parameter values and compute from them the individual parameter configurations of the respective `DataModel`s from this at every step. Thus, this allows for easily connecting different datasets with distinct models while performing simultaneous inference with shared parameters between the models.
