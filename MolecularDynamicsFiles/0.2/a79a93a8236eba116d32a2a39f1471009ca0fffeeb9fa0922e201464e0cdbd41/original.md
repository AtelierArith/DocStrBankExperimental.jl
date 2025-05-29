```julia
velocities(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

Return velocities of particles in the system.

Corresponds to properties `:vx`, `:vy`, `:vz`.
