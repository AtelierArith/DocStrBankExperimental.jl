```
CoordinateVolume(DM::AbstractDataModel, Confnum::Real; N::Int=Int(1e5), WE::Bool=true, Approx::Bool=false, kwargs...) -> Real
```

Computes coordinate-dependent apparent volume of confidence region associated with level `Confnum` via Monte Carlo integration. For likelihoods which are particularly expensive to evaluate, `Approx=true` can improve the performance by approximating the confidence region via polygons.
