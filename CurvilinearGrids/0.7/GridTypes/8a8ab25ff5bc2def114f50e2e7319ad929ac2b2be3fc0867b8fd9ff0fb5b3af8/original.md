```
CurvilinearGrid3D(x, y, z, nhalo::Int; backend=CPU(), discretization_scheme=:MEG6, on_bc=nothing, is_static=false, is_orthogonal=false, tiles=nothing, make_uniform=false)
```

Construct a curvilinear grid in 3D using 3D arrays of x/y/z coordinates.
