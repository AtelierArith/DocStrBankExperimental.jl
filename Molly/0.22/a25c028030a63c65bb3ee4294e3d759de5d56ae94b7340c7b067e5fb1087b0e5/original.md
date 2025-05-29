```
scale_coords!(sys, scale_factor; ignore_molecules=false)
```

Scale the coordinates and bounding box of a system by a scaling factor.

The scaling factor can be a single number or a `SVector` of the appropriate number of dimensions corresponding to the scaling factor for each axis. Velocities are not scaled. If the topology of the system is set then atoms in the same molecule will be moved by the same amount according to the center of coordinates of the molecule. This can be disabled with `ignore_molecules=true`.

Not currently compatible with [`TriclinicBoundary`](@ref) if the topology is set.
