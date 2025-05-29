```
scatter_update(A::Union{SparseTensor, SparseMatrixCSC{Float64,Int64}},
i1::Union{Integer, Colon, UnitRange{T}, PyObject,Array{S,1}},
i2::Union{Integer, Colon, UnitRange{T}, PyObject,Array{T,1}},
B::Union{SparseTensor, SparseMatrixCSC{Float64,Int64}})  where {S<:Real,T<:Real}
```

スパース行列のサブブロックを `B` で更新します。すなわち、 

```
A[i1, i2] = B
```
