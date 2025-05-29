```julia
positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

Return unscaled wrapped positions of particles in the system.

Corresponds to properties `:x`, `:y`, `:z`. Performs conversion from other coordinate representations if needed and possible.
