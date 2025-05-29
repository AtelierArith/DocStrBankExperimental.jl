```
adjoint(o::PyObject; kwargs...)
```

Returns the conjugate adjoint of `o`.  When the dimension of `o` is greater than 2, only the last two dimensions are permuted, i.e., `permutedims(o, [1,2,...,n,n-1])`
