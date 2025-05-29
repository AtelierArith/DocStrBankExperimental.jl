```
Mesh(graphs, Float64; parallel = false, message = nothing)
```

Create a mesh for rendering from an array of `Graph` objects (`graphs`). The graphs may be processed serially (default) or in parallel using multithreading (`parallel = true`). By default, double floating precision will be used (`Float64`) but it is possible to generate a version with a different precision by specifying the corresponding type as in `Mesh(graphs, Float32)`.
