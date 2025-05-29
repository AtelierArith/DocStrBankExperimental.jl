```
onsurface(obj::CSGTree{T}, point::SVector{3,T}) -> Bool
onsurface(obj::CSGTree{T}, x::T, y::T, z::T) -> Bool
```

Tests whether a 3D point in world space is *on* the surface (i.e. shell) of `obj`.
