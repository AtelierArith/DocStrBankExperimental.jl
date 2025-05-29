```
circular_arc(θ, r::T, tolerance; θ_0=0, center=zero(Point{T})) where
            {T <: Coordinate}
```

Discretizes a circular arc to meet a tolerance, ignoring rounding to a grid.

`θ` is the angular position of the end of the arc and `r` is its radius. The maximum distance between any segment and the actual circle will be roughly equal to the tolerance (for small tolerance). Returns an array of Points. Includes both endpoints.

If `θ > θ_0`, the arc is drawn counterclockwise.
