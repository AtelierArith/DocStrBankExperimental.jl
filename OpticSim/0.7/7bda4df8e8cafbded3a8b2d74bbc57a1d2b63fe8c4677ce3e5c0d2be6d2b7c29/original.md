```
inside(surf::ParametricSurface{T}, p::SVector{3,T}) -> Bool
inside(surf::ParametricSurface{T}, x::T, y::T, z::T) -> Bool
```

Tests whether a 3D point in world space is *inside* `surf`.
