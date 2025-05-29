```
MincedBoundaries(DM::AbstractDataModel, Planes::AbstractVector{<:Plane}, Confnum::Real=1.; tol::Real=1e-9, ADmode::Val=Val(:ForwardDiff), meth=Tsit5(), mfd::Bool=false)
```

Intersects the confidence boundary of level `Confnum` with `Planes` and computes `ODESolution`s which parametrize this intersection.
