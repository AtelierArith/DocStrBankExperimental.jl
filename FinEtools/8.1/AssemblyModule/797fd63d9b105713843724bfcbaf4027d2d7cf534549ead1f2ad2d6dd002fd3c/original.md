```
SysmatAssemblerSparse(z = zero(T), nomatrixresult = false) where {T}
```

Construct a sparse system matrix assembler.

The matrix entries are of type `T`. The assembler either produces a sparse matrix (when `nomatrixresult = true`), or does not (when `nomatrixresult = false`). When the assembler does not produce the sparse matrix when `makematrix!` is called, it still can be constructed from the buffers stored in the assembler, until they are cleared when the assembler is destroyed.

# Example

This is how a sparse matrix is assembled from two rectangular dense matrices.

```
    a = SysmatAssemblerSparse(0.0)
    startassembly!(a, 5, 5, 3, 7, 7)
    m = [0.24406   0.599773    0.833404  0.0420141
        0.786024  0.00206713  0.995379  0.780298
        0.845816  0.198459    0.355149  0.224996]
    assemble!(a, m, [1 7 5], [5 2 1 4])
    m = [0.146618  0.53471   0.614342    0.737833
         0.479719  0.41354   0.00760941  0.836455
         0.254868  0.476189  0.460794    0.00919633
         0.159064  0.261821  0.317078    0.77646
         0.643538  0.429817  0.59788     0.958909]
    assemble!(a, m, [2 3 1 7 5], [6 7 3 4])
    A = makematrix!(a)
```

Here `A` is a sparse matrix of the size 7x7.

When the `nomatrixresult` is set as true, no matrix is produced.

```
    a = SysmatAssemblerSparse(0.0, true)
    startassembly!(a, 5, 5, 3, 7, 7)
    m = [0.24406   0.599773    0.833404  0.0420141
        0.786024  0.00206713  0.995379  0.780298
        0.845816  0.198459    0.355149  0.224996]
    assemble!(a, m, [1 7 5], [5 2 1 4])
    m = [0.146618  0.53471   0.614342    0.737833
         0.479719  0.41354   0.00760941  0.836455
         0.254868  0.476189  0.460794    0.00919633
         0.159064  0.261821  0.317078    0.77646
         0.643538  0.429817  0.59788     0.958909]
    assemble!(a, m, [2 3 1 7 5], [6 7 3 4])
    A = makematrix!(a)
```

Here `A` is a named tuple of four sparse zero matrices. To construct the correct matrix is still possible, for instance like this:

```
    a.nomatrixresult = false
    A = makematrix!(a)
```

At this point all the buffers of the assembler have potentially been cleared, and `makematrix!(a)` is no longer possible.
