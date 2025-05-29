```
PredictionEnsemble(DM::AbstractDataModel, pDomain::HyperCube, Xs::AbstractVector{<:Number}=DomainSamples(XCube(DM),300); N::Int=50, uniform::Bool=true, MaxConfnum::Real=3, plot::Bool=isloaded(:Plots), kwargs...)
```

Plots `N` model predictions which are randomly chosen from a confidence region of level `MaxConfnum`.
