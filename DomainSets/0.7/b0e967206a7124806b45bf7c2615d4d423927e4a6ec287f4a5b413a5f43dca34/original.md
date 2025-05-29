```
Ball(radius = 1[, center])
Ball{T,C=:closed}(radius = 1[, center])
```

Return a concrete subtype of `Ball` which represents a ball with the given radius and center, the given eltype `T`, and which is open or closed.

The default center is the origin. In case both radius and center are omitted, a subtype of `UnitBall` is returned, whose concrete type depends on `T`.

A ball represents a volume. For the boundary of a ball, see [`Sphere()`](@ref).
