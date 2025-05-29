```
PlotQuantiles(::Type{<:Distributions.Distribution}, DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLE(DM); kwargs...)
```

指定された `DM` に対する残差の分位数-分位数プロットを指定された分布に対して描画します。
