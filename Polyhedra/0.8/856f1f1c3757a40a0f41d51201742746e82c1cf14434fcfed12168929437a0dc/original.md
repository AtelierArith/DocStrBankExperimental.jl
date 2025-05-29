```
vrep(V::AbstractMatrix, R::AbstractMatrix, Rlinset::BitSet=BitSet())
```

Creates a V-representation for the polyhedron defined by the points $V_i$, lines $R_i$ if `i in Rlinset` and rays $R_i$ otherwise where $V_i$ (resp. $R_i$) is the $i$th row of `V` (resp. `R`), i.e. `V[i,:]` (resp. `R[i,:]`).
