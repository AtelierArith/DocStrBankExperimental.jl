```
PinParameters(DM::AbstractDataModel, Component::Int, Value::AbstractFloat=MLE(DM)[Component])
PinParameters(DM::AbstractDataModel, Components::AbstractVector{<:Int}, Values::AbstractVector{<:AbstractFloat}=MLE(DM)[Components])
PinParameters(DM::AbstractDataModel, ParamDict::Dict{String, Number})
```

Returns `DataModel` where one or more parameters have been pinned to specified values.
