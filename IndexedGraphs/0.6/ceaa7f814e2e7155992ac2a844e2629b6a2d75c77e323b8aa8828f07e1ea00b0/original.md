```
IndexedBiDiGraph{T<:Integer} <: AbstractIndexedDiGraph{T}
```

A type representing a sparse directed graph with access to both outedges and inedges.

### FIELDS

  * `A` – square matrix filled with `NullNumber`s. `A[i,j]` corresponds to edge `j=>i`.
  * `X` – square matrix for efficient access by row. `X[j,i]` points to the index of element `A[i,j]` in `A.nzval`.
