```
Sphere(radius = 1[, center])
Sphere{T}(radius = 1[, center])
```

Return a concrete subtype of `Sphere` which represents a sphere with the given radius and center, and the given eltype `T`.

The default center is the origin. In case both radius and center are omitted, a subtype of `UnitSphere` is returned, whose concrete type depends on `T`.

A sphere represents the boundary of a ball. For the volume, see [`Ball()`](@ref).
