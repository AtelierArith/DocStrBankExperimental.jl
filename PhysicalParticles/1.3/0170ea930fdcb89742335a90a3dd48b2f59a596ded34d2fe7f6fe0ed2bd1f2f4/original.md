```
struct Extent2D{T<:Number} <: AbstractExtent2D{T}
```

Could be constructed by function [`extent`](@ref)

## Fields

  * xMin::T
  * xMax::T
  * yMin::T
  * yMax::T
  * SideLength::T
  * Center::PVector2D{T}
  * Corner::PVector2D{T} : PVector2D(xMin, yMin)
