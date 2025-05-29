```
partials(surf::ParametricSurface{T}, u::T, v::T) -> (SVector{3,T}, SVector{3,T})
partials(surf::ParametricSurface{T}, uv::SVector{2,T}) -> (SVector{3,T}, SVector{3,T})
```

Returns a tuple of the 3D partial derivatives of `surf` with respect to u and v at the given uv coordinate.
