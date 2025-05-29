```
LinearOperator(M::SymTridiagonal{T}, S = Vector{T}) where {T}
```

Constructs a linear operator from a symmetric tridiagonal matrix. If its elements are real, it is also Hermitian, otherwise complex symmetric. Change `S` to use LinearOperators on GPU.
