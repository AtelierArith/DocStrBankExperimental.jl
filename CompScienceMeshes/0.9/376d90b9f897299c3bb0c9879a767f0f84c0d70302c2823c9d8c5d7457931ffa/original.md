```
vertextocellmap(mesh) -> vertextocells, numneighbors
```

Computed an V×M array `vertextocells` where V is the number of vertices and M is the maximum number of cells adjacent to any given vertex such that `vertextocells[v,i]` is the index in the cells of `mesh` of the `i`th cell adjacent to teh `v`-th vertex. `numneighbors[v]` contains the number of cells adjacent to the `v`-th vertex.

This method allows e.g. for the efficient computation of the connectivity matrix of the mesh.
