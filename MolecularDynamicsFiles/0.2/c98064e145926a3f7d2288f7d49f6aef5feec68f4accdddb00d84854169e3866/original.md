```julia
unwrapped_positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

Return unscaled unwrapped positions of particles in the system.

Corresponds to properties `:xu`, `:yu`, `:zu`. Performs conversion from other coordinate representations if needed and possible.
