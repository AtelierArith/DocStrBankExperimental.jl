```julia
system_properties(
    frame::MolecularDynamicsFiles.MDFrame
) -> Dict{Symbol}

```

Return other system properties, such as "units" and "time" of lammps dump or "A" and "R" of CFG.
