```
 regbalance!(A, E; maxiter = 100, tol = 1, pow2 = true) -> (Dl,Dr)
```

Balance the regular pair `(A,E)` by reducing the 1-norm of the matrix `M := abs(A)+abs(E)` by row and column balancing.  This involves diagonal similarity transformations `Dl*(A-λE)*Dr` applied iteratively to `M` to make the rows and columns of `Dl*M*Dr` as close in norm as possible. The [Sinkhorn–Knopp algorithm](https://en.wikipedia.org/wiki/Sinkhorn%27s_theorem) is used  to reduce `M` to a doubly stochastic matrix. 

The resulting `Dl` and `Dr` are diagonal scaling matrices.   If the keyword argument `pow2 = true` is specified, then the components of the resulting  optimal `Dl` and `Dr` are replaced by their nearest integer powers of 2.  If `pow2 = false`, the optimal values `Dl` and `Dr` are returned. The resulting `Dl*A*Dr` and `Dl*E*Dr` overwrite `A` and `E`, respectively

The keyword argument `tol = τ`, with `τ ≤ 1`,  specifies the tolerance used in the stopping criterion.  The iterative process is stopped as soon as the incremental scalings are `tol`-close to the identity. 

The keyword argument `maxiter = k` specifies the maximum number of iterations `k`  allowed in the balancing algorithm. 

*Note:* This function is based on the MATLAB function `rowcolsums.m` of [1], modified such that the scaling operations are directly applied to `A` and `E`.  

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
