```
MRSTWrapMesh(G, N = nothing)
```

Mesh that adapts an exported MRST mesh to the Jutul interface. `G` is assumed to be read directly from file using `MAT.matread`. The raw exported grid can be found under the `data` field.
