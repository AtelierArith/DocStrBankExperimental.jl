```
struct PSparseMatrix{V,B,C,D,T}
```

`PSparseMatrix` (partitioned sparse matrix) is a type representing a matrix whose rows are distributed (a.k.a. partitioned) over different parts for distributed-memory parallel computations. Each part stores a subset of the rows of the matrix and their corresponding non zero columns.

This type overloads numerous array-like operations with corresponding parallel implementations.

# Properties

  * `matrix_partition::A`
  * `row_partition::B`
  * `col_partition::C`
  * `assembled::Bool`

`matrix_partition[i]` contains a (sparse) matrix with the local rows and the corresponding nonzero columns (the local columns) in the part number `i`. `eltype(matrix_partition) == V`. `row_partition[i]` and `col_partition[i]` contain information about the local, own, and ghost rows and columns respectively in part number `i`. The types `eltype(row_partition)` and `eltype(col_partition)` implement the [`AbstractLocalIndices`](@ref) interface. For `assembled==true`, it is assumed that the matrix data is fully contained in the own rows. 

# Supertype hierarchy

```
PSparseMatrix{V,A,B,C,T} <: AbstractMatrix{T}
```

with `T=eltype(V)`.
