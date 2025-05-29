```
UNV3D_mesh(unv_mesh; scale=1, integer_type=Int64, float_type=Float64)
```

Read and convert 3D UNV mesh file into XCALibre.jl. Note that a limitation of the .unv mesh format is that it only supports the following 3D cells:

  * Tetahedrals
  * Prisms
  * Hexahedrals

### Input

  * `unv_mesh` – path to mesh file.

### Optional arguments

  * `scale` – used to scale mesh file e.g. scale=0.001 will convert mesh from mm to metres defaults to 1 i.e. no scaling
  * `integer_type` - select interger type to use in the mesh (Int32 may be useful on GPU runs)
  * `float_type` - select interger type to use in the mesh (Float32 may be useful on GPU runs)
