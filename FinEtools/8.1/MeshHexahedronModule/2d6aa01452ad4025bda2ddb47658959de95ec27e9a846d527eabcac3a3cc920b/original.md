```
T4toH8(fens::FENodeSet, fes::FESetT4)
```

Convert a tetrahedral four-node mesh into eight-node hexahedra.

Each vertex is given one hexahedron. The scheme generates 15 nodes per tetrahedron when creating the hexahedra, one for each edge, one for each face, and one for the interior.
