```
IncrementalTimeSeriesFit(Method::Function, DM::AbstractDataModel, initial::AbstractVector{<:Number}=MLE(DM); steps::Int=length(Data(DM))÷5, kwargs...) -> Vector
```

Uses `Method` for fitting, which should be of the form `(::DataModel, ::AbstractVector) -> ::AbstractVector`
