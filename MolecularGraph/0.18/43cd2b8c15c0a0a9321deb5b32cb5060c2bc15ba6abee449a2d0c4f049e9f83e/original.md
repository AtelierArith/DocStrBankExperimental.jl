```
spacefilling(mol::UndirectedGraph; radii="van der Waals")
```

Represent `mol` as a space-filling (Calotte) model in three dimensions. `mol` should have 3d atom positions represented in Angstroms. (3D SDF files can be downloaded from sites such as PubChem.) The two supported options for `radii` are `"van der Waals"` and `"covalent"`; the former are available only for main-group elements, and the latter are available for all.

This function requires that you load one of the backends of the Makie/GLMakie/CairoMakie family.
