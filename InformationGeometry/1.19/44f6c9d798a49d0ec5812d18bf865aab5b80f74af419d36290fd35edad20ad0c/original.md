```
PlotQuantiles(::Type{<:Distributions.Distribution}, DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLE(DM); kwargs...)
```

Quantile-Quantile plot of the residuals for given `DM` against given Distribution.
