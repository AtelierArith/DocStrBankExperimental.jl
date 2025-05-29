```
ConfidenceRegionVolume(DM::AbstractDataModel, Confnum::Real; N::Int=Int(1e5), WE::Bool=true, Approx::Bool=false, kwargs...) -> Real
```

Computes coordinate-invariant volume of confidence region associated with level `Confnum` via Monte Carlo by integrating the geometric density factor. For likelihoods which are particularly expensive to evaluate, `Approx=true` can improve the performance by approximating the confidence region via polygons.
