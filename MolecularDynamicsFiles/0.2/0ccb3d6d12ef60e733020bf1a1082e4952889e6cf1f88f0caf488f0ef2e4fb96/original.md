```julia
scaled_unwrapped_positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

Return scaled unwrapped positions of particles in the system.

Corresponds to properties `:xsu`, `:ysu`, `:zsu`. Performs conversion from other coordinate representations if needed and possible.
