```
axisymmetric_rtheta_grid(r, θ, discretization_scheme, snap_to_axis, rotational_axis::Symbol, backend=CPU()) -> AxisymmetricGrid2D
```

Create polar grid based on vectors of `r` and `θ` coordinates. The axis of rotation is set by `rotational_axis` as `:x` or `:y`
