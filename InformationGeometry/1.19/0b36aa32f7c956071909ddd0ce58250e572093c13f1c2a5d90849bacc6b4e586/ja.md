```
ParameterPlot(DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLEuncert(DM), Names::AbstractVector{<:AbstractString}=pnames(DM); kwargs...)
ParameterPlot(DM::AbstractDataModel, DM2::AbstractDataModel; kwargs...)
ParameterPlot(X::AbstractVector{T}, Y::AbstractVector{T}, Names::AbstractVector{<:AbstractString}; kwargs...)
```

パラメータ設定の値を比較する散布図。
