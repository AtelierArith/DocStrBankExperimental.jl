```
continuum_limit(prob::CellProblem,
    mesh_points=copy(prob.initial_condition);
    proliferation=false)
```

Returns the `FVMProblem` (if the right boundary is fixed) or  the `MBProblem` (if the right boundary is free) that defines the  continuum limit to the [`CellProblem`](@ref) `prob`. The argument  `mesh_points` defines the mesh points to use for the PDE problem,  which can be a grid of points or a number of points to use. If the problem  should be considered to have proliferation, set `proliferation = true`.
