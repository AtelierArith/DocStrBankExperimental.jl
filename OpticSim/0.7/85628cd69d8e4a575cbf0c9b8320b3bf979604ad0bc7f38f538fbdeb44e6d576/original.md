```
ParaxialInterface{T} <: OpticalInterface{T}
```

Interface describing an idealized planar lens, i.e. one that is thin and with no aberrations.

**In general this interface should not be constructed directly, the `ParaxialLensEllipse` and `ParaxialLensRect` functions should be used to create a [`ParaxialLens`](@ref) object directly.**

```julia
ParaxialInterface(focallength::T, centroid::SVector{3,T}, outsidematerial::Y)
```
