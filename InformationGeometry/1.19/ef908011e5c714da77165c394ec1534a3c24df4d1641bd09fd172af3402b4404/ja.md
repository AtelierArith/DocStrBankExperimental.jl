```
IncrementalTimeSeriesFit(Method::Function, DM::AbstractDataModel, initial::AbstractVector{<:Number}=MLE(DM); steps::Int=length(Data(DM))÷5, kwargs...) -> Vector
```

`Method`をフィッティングに使用します。これは`(::DataModel, ::AbstractVector) -> ::AbstractVector`の形式である必要があります。
