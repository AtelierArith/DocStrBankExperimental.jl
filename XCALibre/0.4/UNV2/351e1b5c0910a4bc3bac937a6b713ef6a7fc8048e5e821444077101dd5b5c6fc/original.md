```
UNV2D_mesh(meshFile; scale=1, integer_type=Int64, float_type=Float64)
```

Read and convert 2D UNV mesh file into XCALibre.jl

### Input

  * `meshFile` – path to mesh file.

### Optional arguments

  * `scale` – used to scale mesh file e.g. scale=0.001 will convert mesh from mm to metres defaults to 1 i.e. no scaling
  * `integer_type` - select interger type to use in the mesh (Int32 may be useful on GPU runs)
  * `float_type` - select interger type to use in the mesh (Float32 may be useful on GPU runs)
