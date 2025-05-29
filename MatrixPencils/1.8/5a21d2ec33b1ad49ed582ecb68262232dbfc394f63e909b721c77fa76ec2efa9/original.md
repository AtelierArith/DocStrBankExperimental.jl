```
pbalance!(M, N; r, c, regpar, shift, maxiter, tol, pow2) -> (Dl, Dr)
```

Balance the `m×n` matrix pencil `M - λN` by reducing the 1-norm of the matrix `T := abs(M)+abs(N)` by row and column balancing.  This involves similarity transformations with diagonal matrices `Dl` and `Dr` applied to `T` to make the rows and columns of `Dl*T*Dr` as close in norm as possible. The modified [Sinkhorn–Knopp algorithm](https://en.wikipedia.org/wiki/Sinkhorn%27s_theorem) described in [1]  is employed to reduce `T` to an approximately doubly stochastic matrix.  The targeted row and column sums can be specified using the keyword arguments `r = rs` and `c = cs`,  where `rs` and `cs` are `m-` and `n-`dimensional positive vectors,  representing the desired row and column sums, respectively (Default: `rs = ones(m)` and `cs = ones(n)`).

The resulting `Dl` and `Dr` are diagonal scaling matrices.   If the keyword argument `pow2 = true` is specified, then the components of the resulting  optimal `Dl` and `Dr` are replaced by their nearest integer powers of 2.  If `pow2 = false`, the optimal values `Dl` and `Dr` are returned. The resulting `Dl*M*Dr` and `Dl*N*Dr` overwrite `M` and `N`, respectively

A regularization-based scaling is performed if a nonzero regularization parameter `α` is specified via the keyword argument `regpar = α`.   If `diagreg = true`, then the balancing algorithm is performed on the extended symmetric matrix `[ α^2*I  T; T' α^2*I ]`, while if `diagreg = false` (default),    the balancing algorithm is performed on the matrix `[ (α/m)^2*em*em'  T; T' (α/n)^2*en*en' ]`,  where `em` and `en` are `m-` and `n-`dimensional vectors with elements equal to one.   If `α = 0` and `shift = γ > 0` is specified, then the algorithm is performed on the rank-one perturbation `T+γ*em*en`. 

The keyword argument `tol = τ`, with `τ ≤ 1`,  specifies the tolerance used in the stopping criterion.  The iterative process is stopped as soon as the incremental scalings are `tol`-close to the identity. 

The keyword argument `maxiter = k` specifies the maximum number of iterations `k`  allowed in the balancing algorithm. 

*Method:* This function employs the regularization approaches proposed in [1], modified  to handle matrices with zero rows or zero columns. The alternative shift based regularization  has been proposed in [2].  

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 

[2] P.A.Knight, The Sinkhorn–Knopp algorithm: Convergence and applications, SIAM J. Matrix     Anal. Appl., 30 (2008), pp. 261–275.   
