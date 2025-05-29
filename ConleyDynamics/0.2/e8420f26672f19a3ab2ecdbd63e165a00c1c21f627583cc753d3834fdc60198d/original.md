```
sparse_identity(n::Int; p::Int=0)
```

Create a sparse identity matrix with n rows and columns.

The optional argument `p` specifies the field characteristic. If `p=0` then the sparse matrix is over the rationals, while if `p>0` is a prime, then the matrix is an integer matrix  whose entries are interpreted in `GF(p)`.
