```
AxisymmetricGrid2D(x::AbstractMatrix{T}, y::AbstractMatrix{T},  nhalo::Int,  snap_to_axis::Bool,  rotational_axis::Symbol;  T=Float64, backend=CPU())
```

Create an axisymmetric 2d grid with `x` and `y` coordinates, with the symmetry axis `rotational_axis = :x` or `rotational_axis = :y`. Enforce coordinates to stay on the axis via `snap_to_axis=True`. The input coordinates do not include halo / ghost data since the geometry is undefined in these regions. The `nhalo` argument defines the number of halo cells along each dimension.
