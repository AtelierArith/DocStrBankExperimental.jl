```
StructureWriter(n_steps, filepath, excluded_res=String[])
```

Write 3D structures to a file in the PDB format throughout a simulation.

The [`System`](@ref) should have `atoms_data` defined. The file will be appended to, so should be deleted before simulation if it already exists.

Not compatible with 2D systems.
