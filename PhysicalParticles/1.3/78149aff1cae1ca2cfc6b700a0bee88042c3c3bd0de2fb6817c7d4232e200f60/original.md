```
struct Extent{T<:Number} <: AbstractExtent3D{T}
```

Could be constructed by function [`extent`](@ref)

## Fields

  * xMin::T
  * xMax::T
  * yMin::T
  * yMax::T
  * zMin::T
  * zMax::T
  * SideLength::T
  * Center::PVector{T}
  * Corner::PVector{T} :  PVector(xMin, yMin, zMin)
