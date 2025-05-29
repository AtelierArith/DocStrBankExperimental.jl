```julia
pbc(
    bc::MolecularDynamicsFiles.BoundaryConditions
) -> Tuple{Bool, Bool, Bool}

```

Return periodic boundary conditions (if the boundary style for each dimension is periodic).
