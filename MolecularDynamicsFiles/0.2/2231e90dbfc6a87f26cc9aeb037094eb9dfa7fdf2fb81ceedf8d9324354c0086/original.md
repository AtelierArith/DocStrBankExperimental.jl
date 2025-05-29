```julia
boxvectors(
    frame::MolecularDynamicsFiles.MDFrame
) -> StaticArraysCore.SMatrix{3, 3, Float64}

```

Return the basis vectors of the simulation box as a matrix. Simulation cell vectors are in the columns.  
