```
opZeros(T, nrow, ncol; S = Vector{T})
opZeros(nrow, ncol)
```

Zero operator of size `nrow`-by-`ncol`, of data type `T` (defaults to `Float64`). Change `S` to use LinearOperators on GPU.
