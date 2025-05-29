```
LocalMultistartFit(DM::AbstractDataModel, scale::Real=sqrt(InvChisqCDF(DOF(DM), ConfVol(2.0))); kwargs...)
LocalMultistartFit(DM::AbstractDataModel, mle::AbstractVector{<:Number}, scale::Real=sqrt(InvChisqCDF(DOF(DM), ConfVol(2.0))); kwargs...)
```

Performs a multistart search locally around a given MLE in a cube constructed from the Fisher information and multiplied with `scale`.
