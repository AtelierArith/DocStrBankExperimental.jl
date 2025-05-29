```julia
pad_vectorfield_mat(
    setup
) -> SparseArrays.SparseMatrixCSC{Tv, Int64} where Tv

```

Create matrix for padding inner vector field with boundary volumes, similar to [`pad_scalarfield_mat`](@ref).
