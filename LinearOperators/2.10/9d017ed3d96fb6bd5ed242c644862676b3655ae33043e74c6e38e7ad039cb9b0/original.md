```
opEye(T, nrow, ncol; S = Vector{T})
opEye(nrow, ncol)
```

Rectangular identity operator of size `nrow`x`ncol` and of data type `T` (defaults to `Float64`). Change `S` to use LinearOperators on GPU.
