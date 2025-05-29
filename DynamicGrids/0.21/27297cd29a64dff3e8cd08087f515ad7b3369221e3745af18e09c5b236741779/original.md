```
BoundaryCondition
```

Abstract supertype for flags that specify the boundary conditions used in the simulation, used in [`inbounds`](@ref) and to update [`NeighborhoodRule`](@ref) grid padding. These determine what happens when a neighborhood or jump extends outside of the grid.
