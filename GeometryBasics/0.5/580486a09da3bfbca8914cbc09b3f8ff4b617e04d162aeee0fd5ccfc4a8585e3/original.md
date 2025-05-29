```
texturecoordinates(primitive)
```

Returns the texturecoordinates of a geometry.

This is allowed to return lazy iterators. Use `decompose_uv(ConcreteVecType, geometry)` (or `decompose_uvw`) to get a `Vector{ConcreteVecType}` with `ConcreteVecType` being something like `Vec2f`.
