```
molecule_centers(coords, boundary, topology)
```

Calculate the coordinates of the center of each molecule in a system.

Accounts for periodic boundary conditions by using the circular mean. If `topology=nothing` then the coordinates are returned.

Not currently compatible with [`TriclinicBoundary`](@ref) if the topology is set.
