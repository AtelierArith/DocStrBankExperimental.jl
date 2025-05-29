```
M = gsylvop(A, B, C, D; mx, nx, htype = false)
```

Define the generalized T-Sylvester operator `M: X -> ∑ A_i*X*B_i + ∑ C_j'*transpose(X)*D_j`, if `htype = false` or the generalized H-Sylvester operator `M: X -> ∑ A_i*X*B_i + ∑ C_j'*X'*D_j`, if `htype = true`. `A_i` and `C_j` are matrices having the same row dimension and `B_i` and `D_j` are matrices having the same column dimension.  `A_i` and `B_i` are contained in the `k`-vectors of matrices `A` and `B`, respectively, and  `C_j` and `D_j` are contained in the `l`-vectors of matrices `C` and `D`, respectively. Any of the component matrices can be given as an `UniformScaling`.  The keyword parameters `mx` and `nx` can be used to specify the row and column dimensions of `X`, if they cannot be inferred from the data.   
