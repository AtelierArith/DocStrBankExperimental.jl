```
circular_arc(θ::Vector, r::T, tolerance; center=zero(Point{T})) where {T <: Coordinate}
```

Discretizes a circular arc of radius `r` from θ[1] to θ[2], choosing the shorter direction (defaults to counterclockwise for a semicircle). `r` is its radius. The maximum distance between any segment and the actual circle will be roughly equal to the tolerance (for small tolerance). Returns an array of Points, including both endpoints.
