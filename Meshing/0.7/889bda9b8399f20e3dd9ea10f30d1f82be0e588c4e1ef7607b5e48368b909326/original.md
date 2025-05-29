```
MarchingCubes(;iso=0.0)
```

Specifies the use of the Marching Cubes algorithm for isosurface extraction. This algorithm provides a good balance between performance and vertex count. In contrast to the other algorithms, vertices may be repeated, so mesh size may be large and it will be difficult to extract topological/connectivity information.

  * `iso` (default: 0.0) specifies the iso level to use for surface extraction.
