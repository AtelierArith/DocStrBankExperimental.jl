```
CurvilinearGrid2D(x::AbstractArray{T,2}, y::AbstractArray{T,2}, nhalo::Int, discretization_scheme=:MEG6; backend=CPU()) where {T}
```

Create a 2d grid with `x` and `y` coordinates. The input coordinates do not include halo / ghost data since the geometry is undefined in these regions. The `nhalo` argument defines the number of halo cells along each dimension.
