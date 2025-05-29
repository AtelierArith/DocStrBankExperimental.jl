```julia
SparseMatrixCSB(
    A::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer}
) -> CompressedSparseBlocks.SparseMatrixCSB{Tv, Ti} where {Tv, Ti<:Integer}
SparseMatrixCSB(
    A::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer},
    beta::Integer
) -> CompressedSparseBlocks.SparseMatrixCSB{Tv, Ti} where {Tv, Ti<:Integer}

```

Convert a `SparseMatrixCSC` matrix `A` into a `SparseMatrixCSB` matrix.

# Optional arguments

  * `beta`: The size of each block in base-2 logarithm; if 0 the package decides the block size internally.
