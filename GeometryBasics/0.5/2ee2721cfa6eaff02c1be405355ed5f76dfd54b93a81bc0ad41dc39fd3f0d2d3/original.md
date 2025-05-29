```
coordinates(geometry)
```

Returns the positions/coordinates of a geometry.

This is allowed to return lazy iterators. Use `decompose(ConcretePointType, geometry)` to get a `Vector{ConcretePointType}` with `ConcretePointType` being something like `Point3f`.
