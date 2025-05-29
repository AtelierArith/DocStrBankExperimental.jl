```
ParameterPlot(DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLEuncert(DM), Names::AbstractVector{<:AbstractString}=pnames(DM); kwargs...)
ParameterPlot(DM::AbstractDataModel, DM2::AbstractDataModel; kwargs...)
ParameterPlot(X::AbstractVector{T}, Y::AbstractVector{T}, Names::AbstractVector{<:AbstractString}; kwargs...)
```

Scatter plot comparing the values of parameter configurations.
