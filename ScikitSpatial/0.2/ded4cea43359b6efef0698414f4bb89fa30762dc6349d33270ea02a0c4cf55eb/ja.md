```
project(point::AbstractVector, plane::AbstractPlane) -> StaticArrays.SVector
```

点を平面に投影します。

# 例

```jldoctest
julia> project([0, 0, 5], Plane([0, 0, 0], [0, 0, 1]))
3-element StaticArrays.SVector{3, Float64} with indices SOneTo(3):
 0.0
 0.0
 0.0

julia> plane = Plane([1,2,3], [1, 3, -2]);

julia> point_projected = project([5, 1, 3], plane);

julia> round.(point_projected, digits=3)
3-element StaticArrays.SVector{3, Float64} with indices SOneTo(3):
 4.929
 0.786
 3.143
```
