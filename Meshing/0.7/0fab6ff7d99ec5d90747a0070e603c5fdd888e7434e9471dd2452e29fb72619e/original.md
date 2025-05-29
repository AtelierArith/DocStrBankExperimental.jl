```
MarchingTetrahedra(;iso=0.0, eps=1e-3)
```

Specifies the use of the Marching Tetrahedra algorithm for isosurface extraction. This algorithm generates more faces. However, each vertex is guaranteed to not be repeated, making this algorithm useful for topological analysis.

  * `iso` specifies the iso level to use for surface extraction.
  * `eps` is the tolerence around a voxel corner to ensure manifold mesh generation.
