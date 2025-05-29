```
ProjectionSparseMatrixExp{N, MN1<:AbstractSparseMatrix{N},
                             MN2<:AbstractSparseMatrix{N},
                             MN3<:AbstractSparseMatrix{N}}
```

Type that represents the projection of a sparse matrix exponential, i.e., $L⋅\exp(M)⋅R$ for a given sparse matrix $M$.

### Fields

  * `L` – left multiplication matrix
  * `E` – sparse matrix exponential
  * `R` – right multiplication matrix
