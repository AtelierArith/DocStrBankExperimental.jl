```
FindConfBoundaryOnPlane(DM::AbstractDataModel,PL::Plane,Confnum::Real=1.; tol::Real=1e-8) -> Union{AbstractVector{<:Number},Bool}
```

Computes point inside the plane `PL` which lies on the boundary of a confidence region of level `Confnum`. If such a point cannot be found (i.e. does not seem to exist), the method returns `false`.
