```
dualconnectionmatrix(
    self::FEMM,
    fens::FENodeSet,
    minnodes = 1,
) where {FEMM<:AbstractFEMM}
```

Compute the dual connection matrix.

The matrix has a nonzero in all the rows and columns which correspond to elements connected by some finite element nodes.

  * `minnodes`: minimum number of nodes that the elements needs to share in order to be neighbors (default 1)
