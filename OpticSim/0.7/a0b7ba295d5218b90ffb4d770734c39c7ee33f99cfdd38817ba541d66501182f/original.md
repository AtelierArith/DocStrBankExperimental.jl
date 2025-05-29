```
normal(surf::ParametricSurface{T}, u::T, v::T) -> SVector{3,T}
normal(surf::ParametricSurface{T}, uv::SVector{2,T}) -> SVector{3,T}
```

Returns the normal to `surf` at the given uv coordinate.
