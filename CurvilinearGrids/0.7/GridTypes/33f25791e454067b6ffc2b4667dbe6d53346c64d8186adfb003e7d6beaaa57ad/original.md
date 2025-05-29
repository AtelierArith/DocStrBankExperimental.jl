```
rtheta_grid((r0, θ0), (r1, θ1), (ni_cells, nj_cells), discretization_scheme, snap_to_axis, rotational_axis, backend=CPU(), T=Float64) -> AxisymmetricGrid2D
```

Create an equally spaced axisymmetric polar grid based on `r` and `θ`. The axis of rotation is set by `rotational_axis` as `:x` or `:y`
