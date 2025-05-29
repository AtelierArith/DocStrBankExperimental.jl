```
LinearOperator(M::AbstractMatrix{T}; symmetric=false, hermitian=false, S = Vector{T}) where {T}
```

Construct a linear operator from a dense or sparse matrix. Use the optional keyword arguments to indicate whether the operator is symmetric and/or hermitian. Change `S` to use LinearOperators on GPU.
