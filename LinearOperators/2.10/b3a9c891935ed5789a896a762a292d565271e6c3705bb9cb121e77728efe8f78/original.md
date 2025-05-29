```
opOnes(T, nrow, ncol; S = Vector{T})
opOnes(nrow, ncol)
```

Operator of all ones of size `nrow`-by-`ncol` of data type `T` (defaults to `Float64`). Change `S` to use LinearOperators on GPU.
