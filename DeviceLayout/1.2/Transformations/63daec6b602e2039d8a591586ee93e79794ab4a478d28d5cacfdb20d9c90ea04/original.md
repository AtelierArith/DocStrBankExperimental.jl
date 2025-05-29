```
origin(f::Transformation)
```

Return the transformed origin if it is translated, or `nothing` otherwise.

It's necessary to return `nothing` rather than a `zero(Point{T})` if there's no translation, because such transformations (e.g., `LinearMap`s) may not supply a coordinate type `T`.
