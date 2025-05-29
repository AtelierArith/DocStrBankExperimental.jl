```
struct Extent2D{T<:Number} <: AbstractExtent2D{T}
```

は関数 [`extent`](@ref) によって構築される可能性があります。

## フィールド

  * xMin::T
  * xMax::T
  * yMin::T
  * yMax::T
  * SideLength::T
  * Center::PVector2D{T}
  * Corner::PVector2D{T} : PVector2D(xMin, yMin)
