```
T4refine20(fens::FENodeSet, fes::FESetT4)
```

Refine a tetrahedral four-node mesh into another four-node tetrahedral mesh, with each original tetrahedron being subdivided into 20 new tetrahedra.

Each vertex is given one hexahedron. The scheme generates 15 nodes per tetrahedron when creating the hexahedra, one for each edge, one for each face, and one for the interior.
