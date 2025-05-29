```
PredictionEnsemble(DM::AbstractDataModel, pDomain::HyperCube, Xs::AbstractVector{<:Number}=DomainSamples(XCube(DM),300); N::Int=50, uniform::Bool=true, MaxConfnum::Real=3, plot::Bool=isloaded(:Plots), kwargs...)
```

レベル `MaxConfnum` の信頼領域からランダムに選ばれた `N` 個のモデル予測をプロットします。
