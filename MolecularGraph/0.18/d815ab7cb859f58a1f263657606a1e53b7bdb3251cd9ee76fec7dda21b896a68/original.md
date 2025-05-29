```
ballstick(mol::UndirectedGraph; radii=0.3, bonddiameter=0.1)
```

Represent `mol` as a ball-and-stick model in three dimensions. `mol` should have 3d atom positions represented in Angstroms. 3D SDF files can be downloaded from sites such as PubChem.

`radii` optionally specifies the radii of the balls, in Angstroms. `bonddiameter` optionally specifies the radii of the sticks, in Angstroms.

This function requires that you load one of the backends of the Makie/GLMakie/CairoMakie family.
