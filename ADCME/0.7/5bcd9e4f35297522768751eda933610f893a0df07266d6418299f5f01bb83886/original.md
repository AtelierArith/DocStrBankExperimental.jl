```
factorize(A::Union{SparseTensor, SparseMatrixCSC}, max_cache_size::Int64 = 999999)
```

Factorizes $A$ for sparse matrix solutions. `max_cache_size` specifies the maximum cache sizes in the C++ kernels,  which determines the maximum number of factorized matrices.  The function returns the factorized matrix, which is basically `Tuple{SparseTensor, PyObject}`. 

# Example

```julia
A = sprand(10,10,0.7)
Afac = factorize(A) # factorizing the matrix
run(sess, Afac\rand(10)) # no factorization, solving the equation
run(sess, Afac\rand(10)) # no factorization, solving the equation
```
