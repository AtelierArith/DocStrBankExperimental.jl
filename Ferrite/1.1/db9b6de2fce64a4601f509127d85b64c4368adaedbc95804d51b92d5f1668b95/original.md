```
struct BlockSparsityPattern <: AbstractSparsityPattern
```

Data structure representing non-zero entries for an eventual *blocked* sparse matrix.

See the constructor [`BlockSparsityPattern(::Vector{Int})`](@ref BlockSparsityPattern(::Vector{Int})) for the user-facing documentation.

# Struct fields

  * `nrows::Int`: number of rows
  * `ncols::Int`: number of column
  * `block_sizes::Vector{Int}`: row and column block sizes
  * `blocks::Matrix{SparsityPattern}`: matrix of size `length(block_sizes) × length(block_sizes)` where `blocks[i, j]` is a [`SparsityPattern`](@ref) corresponding to block `(i, j)`.

!!! warning "Internal struct"
    The specific implementation of this struct, such as struct fields, type layout and type parameters, are internal and should not be relied upon.

