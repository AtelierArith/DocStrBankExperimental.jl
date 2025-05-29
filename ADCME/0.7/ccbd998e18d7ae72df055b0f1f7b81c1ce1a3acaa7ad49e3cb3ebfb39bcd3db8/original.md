```
solve(A_factorized::Tuple{SparseTensor, PyObject}, rhs::Union{Array{Float64,1}, PyObject})
```

Solves the equation `A_factorized * x = rhs` using the factorized sparse matrix. See [`factorize`](@ref).
