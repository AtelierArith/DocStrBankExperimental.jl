```
mul_sparse(A::SMat{T}, B::SMat{T}) -> SMat{T}
```

Return the product $A\cdot B$ as a sparse matrix.

The product of two sparse matrices is, in general, not sparse, so depending on the context, it might be more efficient to use [`mul_dense(::SMat{T}, ::SMat{T}) where {T}`](@ref) instead.
