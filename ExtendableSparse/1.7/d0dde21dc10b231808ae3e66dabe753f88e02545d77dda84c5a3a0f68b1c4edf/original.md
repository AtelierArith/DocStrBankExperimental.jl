```julia
mutable struct SparseMatrixLNK{Tv, Ti<:Integer} <: ExtendableSparse.AbstractSparseMatrixExtension{Tv, Ti<:Integer}
```

Struct to hold sparse matrix in the linked list format.

Modeled after the linked list sparse matrix format described in  the  [whitepaper](https://www-users.cs.umn.edu/~saad/software/SPARSKIT/paper.ps) and the  [SPARSEKIT2 source code](https://www-users.cs.umn.edu/~saad/software/SPARSKIT/SPARSKIT2.tar.gz) by Y. Saad. He writes "This is one of the oldest data structures used for sparse matrix computations."

The relevant source [formats.f](https://salsa.debian.org/science-team/sparskit/blob/master/FORMATS/formats.f) is also available in the debian/science gitlab.

The advantage of the linked list structure is the fact that upon insertion of a new entry, the arrays describing the structure can grow at their respective ends and can be conveniently updated via `push!`.  No copying of existing data is necessary.

  * `m::Integer`: Number of rows

  * `n::Integer`: Number of columns

  * `nnz::Integer`: Number of nonzeros

  * `nentries::Integer`: Length of arrays

  * `colptr::Vector{Ti} where Ti<:Integer`: Linked list of column entries. Initial length is n, it grows with each new entry.

    colptr[index] contains the next index in the list or zero, in the later case terminating the list which starts at index 1<=j<=n for each column j.

  * `rowval::Vector{Ti} where Ti<:Integer`: Row numbers. For each index it contains the zero (initial state) or the row numbers corresponding to the column entry list in colptr.

    Initial length is n, it grows with each new entry.

  * `nzval::Vector`: Nonzero entry values corresponding to each pair (colptr[index],rowval[index])

    Initial length is n,  it grows with each new entry.
