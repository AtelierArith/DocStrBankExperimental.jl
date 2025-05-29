```
coordinates(geometry)
```

Returns the edges/vertices/coordinates of a geometry. Is allowed to return lazy iterators! Use `decompose(ConcretePointType, geometry)` to get `Vector{ConcretePointType}` with `ConcretePointType` to be something like `Point{3, Float32}`.
