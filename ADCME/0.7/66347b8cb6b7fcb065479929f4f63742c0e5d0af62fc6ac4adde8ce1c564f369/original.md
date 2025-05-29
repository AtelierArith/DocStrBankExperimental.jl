```
scatter_update(A::Union{SparseTensor, SparseMatrixCSC{Float64,Int64}},
i1::Union{Integer, Colon, UnitRange{T}, PyObject,Array{S,1}},
i2::Union{Integer, Colon, UnitRange{T}, PyObject,Array{T,1}},
B::Union{SparseTensor, SparseMatrixCSC{Float64,Int64}})  where {S<:Real,T<:Real}
```

Updates a subblock of a sparse matrix by `B`. Equivalently, 

```
A[i1, i2] = B
```
