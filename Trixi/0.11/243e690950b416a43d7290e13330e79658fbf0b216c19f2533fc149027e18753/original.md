```
struct NoSlip
```

Use to create a no-slip boundary condition with [`BoundaryConditionNavierStokesWall`](@ref).  The field `boundary_value_function` should be a function with signature  `boundary_value_function(x, t, equations)` and return a `SVector{NDIMS}`  whose entries are the velocity vector at a point `x` and time `t`.
