```julia
updateindex!(ext, op, v, i, j)

```

Update element of the matrix  with operation `op`. This can replace the following code and save one index search during acces:

```@example
using ExtendableSparse # hide
A=ExtendableSparseMatrix(3,3)
A[1,2]+=0.1
A
```

```@example
using ExtendableSparse # hide

A=ExtendableSparseMatrix(3,3)
updateindex!(A,+,0.1,1,2)
A
```

If `v` is zero, no new entry is created.
