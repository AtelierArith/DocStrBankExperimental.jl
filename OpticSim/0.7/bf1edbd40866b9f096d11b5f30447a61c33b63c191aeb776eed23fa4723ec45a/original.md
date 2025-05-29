```
inside(obj::CSGTree{T}, point::SVector{3,T}) -> Bool
inside(obj::CSGTree{T}, x::T, y::T, z::T) -> Bool
```

Tests whether a 3D point in world space is *inside* `obj`.
