```
vector_1D(c1, c2, side_length)
```

Displacement between two 1D coordinate values from c1 to c2, accounting for periodic boundary conditions in a [`CubicBoundary`](@ref) or [`RectangularBoundary`](@ref).

The minimum image convention is used, so the displacement is to the closest version of the coordinate accounting for the periodic boundaries.
