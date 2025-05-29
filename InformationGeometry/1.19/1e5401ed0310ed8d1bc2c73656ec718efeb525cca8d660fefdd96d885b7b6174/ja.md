```
PinParameters(DM::AbstractDataModel, Component::Int, Value::AbstractFloat=MLE(DM)[Component])
PinParameters(DM::AbstractDataModel, Components::AbstractVector{<:Int}, Values::AbstractVector{<:AbstractFloat}=MLE(DM)[Components])
PinParameters(DM::AbstractDataModel, ParamDict::Dict{String, Number})
```

指定された値にピン留めされた1つ以上のパラメータを持つ`DataModel`を返します。
