```
kron_reduce(M::AbstractMatrix)::Matrix
```

Given a 4x4 matrix remove the 4th row and column to create a 3x3 matrix.

The new values in the 3x3 are:

```julia
M_new[i,j] = M[i,j] - M[i,4] *  M[4,j] / M[4,4]  
```

where `i` and `j` are in the `Set((1,2,3))`.
