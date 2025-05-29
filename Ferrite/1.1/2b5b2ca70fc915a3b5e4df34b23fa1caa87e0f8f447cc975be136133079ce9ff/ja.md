```
allocate_matrix(dh::DofHandler, args...; kwargs...)
```

DofHandler `dh` から `SparseMatrixCSC{Float64, Int}` 型の行列を割り当てます。

このメソッドは、同等の [`allocate_matrix(SparseMatrixCSC{Float64, Int}, dh, args...; kwargs...)`](@ref allocate_matrix(::Type{MatrixType}, ::DofHandler, args...; kwargs...) where {MatrixType}) のショートハンドです – 詳細についてはそのメソッドを参照してください。
