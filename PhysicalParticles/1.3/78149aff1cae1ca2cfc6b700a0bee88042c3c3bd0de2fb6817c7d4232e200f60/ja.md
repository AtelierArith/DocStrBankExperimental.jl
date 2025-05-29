```
struct Extent{T<:Number} <: AbstractExtent3D{T}
```

関数 [`extent`](@ref) によって構築される可能性があります

## フィールド

  * xMin::T
  * xMax::T
  * yMin::T
  * yMax::T
  * zMin::T
  * zMax::T
  * SideLength::T
  * Center::PVector{T}
  * Corner::PVector{T} :  PVector(xMin, yMin, zMin)
