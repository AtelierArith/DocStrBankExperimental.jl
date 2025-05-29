```
struct MeshMap
```

Mapping from full mesh to irreducible mesh. The reduction is mainly available via symmetry operations.

# Parameters:

  * `map`: mapping from full mesh to irreducible mesh. When i is the index of a point in the full mesh, map[i] is the corresponding index in reduced mesh
  * `reduced_length`: the length of reduced mesh
  * `inv_map`: inverse of map. When i is the index of a point in the reduced mesh, inv_map[i] is a list of all points corresponding to this point in the full mesh
