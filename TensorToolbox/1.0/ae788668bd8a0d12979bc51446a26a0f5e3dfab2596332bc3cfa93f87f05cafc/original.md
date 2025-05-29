```
cp_als(X,R;init,tol,maxit,dimorder)
```

Compute a CP decomposition with R components of a tensor X .

## Arguments:

  * `init` ∈ {MatrixCell,"rand","nvecs","eigs"}. Initial guess for factor matrices. If init="nvecs" (same as "eigs") initialize matrices with function nvecs.
  * `tol`: Tolerance. Defualt: 1e-4.
  * `maxit`: Maximal number of iterations. Default: 1000.
  * `dimorder': Order of dimensions. Default: 1:ndims(A).
