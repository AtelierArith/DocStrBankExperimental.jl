```
Interpolation(x, y, gridargs...; method::Symbol = :linear, kwargs...)
```

Create an interpolation scheme from a set of `x` values and `y` values (to be interpolated).  `method` sets the interpolation type, and `extrapolation_bc` sets the extrapolation  boundary condition (either a valid `BoundaryCondition` or `NaN`).
