```
vector(c1, c2, boundary)
```

Displacement between two coordinate values from c1 to c2, accounting for periodic boundary conditions.

The minimum image convention is used, so the displacement is to the closest version of the coordinates accounting for the periodic boundaries. For the [`TriclinicBoundary`](@ref) an approximation is used to find the closest version by default.
