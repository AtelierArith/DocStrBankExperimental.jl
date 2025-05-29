```
raviartthomas(mesh)
```

Conducts pre-processing on the input `mesh` by extracting the cell edges, cell pairs     and indices required to construct the RT basis on the `mesh`.

Calls raviartthomas(mesh::Mesh, cellpairs::Array{Int,2}), which constructs     the RT basis on the `mesh`, using the cell pairs identified.

Returns the RT basis object.
