```
struct Point{T<:PointTypes} <: StaticArrays.FieldVector{2,T}
    x::T
    y::T
end
```

2D Cartesian coordinate in the plane.
