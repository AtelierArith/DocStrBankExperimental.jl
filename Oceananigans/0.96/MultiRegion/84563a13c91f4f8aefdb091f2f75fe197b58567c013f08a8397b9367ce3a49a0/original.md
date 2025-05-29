```
ConformalCubedSphereGrid(filepath::AbstractString, arch::AbstractArchitecture=CPU(), FT=Float64;
                         Nz,
                         z,
                         panel_halo = (4, 4, 4),
                         panel_topology = (FullyConnected, FullyConnected, Bounded),
                         radius = R_Earth,
                         devices = nothing)
```

Load a `ConformalCubedSphereGrid` from `filepath`.
