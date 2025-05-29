```
CoarseMesh(G::JutulMesh, p)
```

Construct a coarse mesh from a given `JutulMesh` that can be converted to an `UnstructuredMesh` instance. The second argument `p` should be a partition Vector with one entry per cell in the original grid that assigns that cell to a coarse block. Should be one-indexed and the numbering should be sequential and contain at least one fine cell for each coarse index. This is tested by the function.
