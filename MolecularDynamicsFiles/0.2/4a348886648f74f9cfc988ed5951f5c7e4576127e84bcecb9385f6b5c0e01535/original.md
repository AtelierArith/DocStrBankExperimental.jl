```julia
particle_types(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{Int64}

```

Return particle types.

Corresponds to property `:type`. If there's no particle type data in the frame, attempts to generate from 1) elements of particles 2) masses of particles.
