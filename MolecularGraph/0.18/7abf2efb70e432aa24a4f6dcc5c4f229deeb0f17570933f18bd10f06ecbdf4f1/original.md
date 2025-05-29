```
stick(mol::UndirectedGraph; size=0.3)
```

Represent `mol` as a stick model in three dimensions. `mol` should have 3d atom positions represented in Angstroms. 3D SDF files can be downloaded from sites such as PubChem.

`size` optionally specifies the width of the sticks, in Angstroms.

This function requires that you load one of the backends of the Makie/GLMakie/CairoMakie family.
