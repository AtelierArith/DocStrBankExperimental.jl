```
IntersectRegion(DM::AbstractDataModel,PL::Plane,v::AbstractVector{<:Number},Confnum::Real=1.; N::Int=31) -> Vector{Plane}
```

Translates family of `N` planes which are translated approximately from `-v` to `+v` and intersect the confidence region of level `Confnum`. If necessary, planes are removed or more planes added such that the maximal family of planes is found.
