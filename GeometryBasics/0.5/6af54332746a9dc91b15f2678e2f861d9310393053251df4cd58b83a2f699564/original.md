```
faces(geometry)
```

Returns the faces of a geometry.

This is allowed to return lazy iterators. Use `decompose(ConcreteFaceType, geometry)` to get a `Vector{ConcreteFaceType}` with `ConcreteFaceType` being something like `GLTriangleFace`.
