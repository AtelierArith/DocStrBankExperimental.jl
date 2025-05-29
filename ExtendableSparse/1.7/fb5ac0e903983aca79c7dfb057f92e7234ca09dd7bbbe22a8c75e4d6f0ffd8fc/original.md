```julia
mutable struct ExtendableSparseMatrixCSC{Tv, Ti<:Integer} <: ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti<:Integer}
```

Extendable sparse matrix. A nonzero  entry of this matrix is contained either in cscmatrix, or in lnkmatrix, never in both.

  * `cscmatrix::SparseArrays.SparseMatrixCSC`: Final matrix data

  * `lnkmatrix::Union{Nothing, ExtendableSparse.SparseMatrixLNK{Tv, Ti}} where {Tv, Ti<:Integer}`: Linked list structure holding data of extension

  * `phash::UInt64`: Pattern hash
