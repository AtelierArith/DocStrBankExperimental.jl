```
connectionmatrix(self::FEMM, nnodes) where {FEMM<:AbstractFEMM}
```

Compute the connection matrix.

The matrix has a nonzero in all the rows and columns which correspond to nodes connected by some finite element.
