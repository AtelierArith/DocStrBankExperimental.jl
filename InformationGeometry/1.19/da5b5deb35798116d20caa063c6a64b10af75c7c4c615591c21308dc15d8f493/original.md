```
ConfidenceRegion(DM::AbstractDataModel, Confnum::Real=1.; tol::Real=1e-9, meth=Tsit5(), mfd::Bool=false, ADmode::Val=Val(:ForwardDiff), parallel::Bool=false, Dirs::Tuple{Int,Int,Int}=(1,2,3), N::Int=30)
```

Computes confidence region of level `Confnum`. For `pdim(DM) > 2`, the confidence region is intersected by a family of `Plane`s in the directions specified by the keyword `Dirs`. The `Plane`s and their embedded 2D confidence boundaries are returned as the respective first and second arguments in this case.
