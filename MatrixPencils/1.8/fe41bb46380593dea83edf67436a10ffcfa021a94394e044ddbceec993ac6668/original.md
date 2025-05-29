```
rcsumsbal!(M; shift, r, c, maxiter, tol) -> (Dl,Dr)
```

Perform the Sinkhorn-Knopp-like algorithm to scale  a non-negative matrix `M` such that `Dl*M*Dr` has column sums equal to a positive row vector `cs` and row sums equal to a  positive column vector `rs`, where `sum(c) = sum(r)`.  If shift = γ > 0 is specified, the algorithm is performed on the rank-one perturbation `M+γ*e1*e2`,  where `e1` and `e2` are vectors  of ones of appropriate dimensions.  The iterative process is stopped as soon as the incremental scalings are `tol`-close to the identity.   `maxiter` is the maximum number of allowed iterations and `tol` is the tolerance for the transformation updates. 

The resulting `Dl*M*Dr` overwrites `M` and is a matrix with equal row sums and  equal column sums. `Dl` and `Dr` are the diagonal scaling matrices. 

*Note:* This function is based on the MATLAB function `rowcolsums.m` of [1], modified  to handle matrices with zero rows or columns. The implemented shift based regularization  has been proposed in [2].  

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 

[2] P.A.Knight, The Sinkhorn–Knopp algorithm: Convergence and applications, SIAM J. Matrix     Anal. Appl., 30 (2008), pp. 261–275.   
