```
point(surf::ParametricSurface{T}, u::T, v::T) -> SVector{3,T}
point(surf::ParametricSurface{T}, uv::SVector{2,T}) -> SVector{3,T}
```

Returns the 3D point on `surf` at the given uv coordinate.
