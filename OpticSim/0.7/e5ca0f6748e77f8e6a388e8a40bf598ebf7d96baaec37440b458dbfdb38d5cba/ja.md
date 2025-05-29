```
BoundingBox{T<:Real}
```

軸に整列した三次元バウンディングボックス。

```julia
BoundingBox(xmin::T, xmax::T, ymin::T, ymax::T, zmin::T, zmax::T)
BoundingBox(s::Surface{T})
BoundingBox(s::ParametricSurface{T,3}, transform::Transform{T} = identitytransform(T))
BoundingBox(c::CSGTree{T})
BoundingBox(tri::Triangle{T})
BoundingBox(triangles::AbstractVector{Triangle{T}})
BoundingBox(points::AbstractArray{SVector{3,T}})
BoundingBox(la::LensAssembly{T})
```
