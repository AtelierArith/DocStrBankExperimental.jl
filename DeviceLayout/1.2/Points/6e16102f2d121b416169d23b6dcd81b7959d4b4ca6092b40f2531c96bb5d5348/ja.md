```
struct Point{T<:PointTypes} <: StaticArrays.FieldVector{2,T}
    x::T
    y::T
end
```

平面の2Dデカルト座標。
