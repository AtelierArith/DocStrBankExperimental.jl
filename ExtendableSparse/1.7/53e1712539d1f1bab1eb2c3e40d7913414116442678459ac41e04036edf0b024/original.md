```julia
rawupdateindex!(lnk, op, v, i, j)

```

Update element of the matrix  with operation `op`.  It assumes that `op(0,0)==0`. If `v` is zero a new entry is created nevertheless.
