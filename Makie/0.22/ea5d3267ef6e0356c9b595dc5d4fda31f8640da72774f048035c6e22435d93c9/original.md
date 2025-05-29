```
Plane(point::Point, normal::Vec)
Plane(normal::Vec, distance::Real)
```

Creates a Plane with the given `normal` containing the given `point`. The internal representation uses a `distance = dot(point, normal)` which can also be constructed directly.
