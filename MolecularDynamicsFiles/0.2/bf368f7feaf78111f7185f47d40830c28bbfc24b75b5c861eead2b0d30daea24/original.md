```julia
scaled_positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

Return scaled wrapped positions of particles in the system.

Corresponds to properties `:xs`, `:ys`, `:zs`. Performs conversion from other coordinate representations if needed and possible.
