```
SysmatAssemblerSparseSymm(z::T, nomatrixresult = false) where {T}
```

Construct blank system matrix assembler for symmetric matrices. The matrix entries are of type `T`.

# Example

This is how a symmetric sparse matrix is assembled from two square dense matrices.

```
    a = SysmatAssemblerSparseSymm(0.0)
    startassembly!(a, 5, 5, 3, 7, 7)
    m = [0.24406   0.599773    0.833404  0.0420141
        0.786024  0.00206713  0.995379  0.780298
        0.845816  0.198459    0.355149  0.224996]
    assemble!(a, m'*m, [5 2 1 4], [5 2 1 4])
    m = [0.146618  0.53471   0.614342    0.737833
         0.479719  0.41354   0.00760941  0.836455
         0.254868  0.476189  0.460794    0.00919633
         0.159064  0.261821  0.317078    0.77646
         0.643538  0.429817  0.59788     0.958909]
    assemble!(a, m'*m, [2 3 1 5], [2 3 1 5])
    A = makematrix!(a)
```

# See also

SysmatAssemblerSparse
