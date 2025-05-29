```
struct SparsityPattern <: AbstractSparsityPattern
```

Data structure representing non-zero entries in the eventual sparse matrix.

See the constructor [`SparsityPattern(::Int, ::Int)`](@ref) for the user-facing documentation.

# Struct fields

  * `nrows::Int`: number of rows
  * `ncols::Int`: number of column
  * `rows::Vector{Vector{Int}}`: vector of length `nrows`, where `rows[i]` is a *sorted* vector of column indices for non zero entries in row `i`.

!!! warning "Internal struct"
    The specific implementation of this struct, such as struct fields, type layout and type parameters, are internal and should not be relied upon.

