```
IndexedDiGraph{T<:Integer} <: AbstractIndexedDiGraph{T}
```

A type representing a sparse directed graph with access only to outedges.

### FIELDS

  * `A` – square matrix filled with `NullNumber`s. `A[i,j]` corresponds to an edge `j=>i`
