```julia
mol_tags(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{Int64}

```

Return ids of the molecules that the particles belong to.

Corresponds to property `:mol`.
