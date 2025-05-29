```
normals(primitive)
```

Returns the normals of a geometry.

This is allowed to return lazy iterators. Use `decompose_normals(ConcreteVecType, geometry)` to get a `Vector{ConcreteVecType}` with `ConcreteVecType` being something like `Vec3f`.
