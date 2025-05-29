```
allocate_matrix(dh::DofHandler, args...; kwargs...)
```

Allocate a matrix of type `SparseMatrixCSC{Float64, Int}` from the DofHandler `dh`.

This method is a shorthand for the equivalent [`allocate_matrix(SparseMatrixCSC{Float64, Int}, dh, args...; kwargs...)`](@ref allocate_matrix(::Type{MatrixType}, ::DofHandler, args...; kwargs...) where {MatrixType}) – refer to that method for details.
