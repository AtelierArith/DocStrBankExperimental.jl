```
 gtsylvi(A, B, C, D, E; mx, nx, abstol, reltol, maxiter) -> (X,info)
```

Compute a solution `X` of the generalized T-Sylvester matrix equation

```
  ∑ A_i*X*B_i + ∑ C_j*transpose(X)*D_j = E,
```

where `A_i` and `C_j` are matrices having the same row dimension equal to the row dimension of `E` and  `B_i` and `D_j` are matrices having the same column dimension equal to the column dimension of `E`.  `A_i` and `B_i` are contained in the `k`-vectors of matrices `A` and `B`, respectively, and  `C_j` and `D_j` are contained in the `l`-vectors of matrices `C` and `D`, respectively.  Any of the component matrices can be given as an `UniformScaling`.  The keyword parameters `mx` and `nx` can be used to specify the row and column dimensions of `X`,  if they cannot be inferred from the data.

A least-squares solution `X` is determined using a conjugate-gradient based iterative method applied  to a suitably defined T-Sylvester linear operator `L:X -> Y` such that `L(X) = E` or `norm(L(X) - E)` is minimized.  The keyword arguments `abstol` (default: `abstol = 0`) and `reltol` (default: `reltol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution and  the keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 1000`). 

*Note:* For the derivation of the adjoint equation see reference [1], which also served as motivation to implement a general linear matrix equation solver in Julia.  

[1] Uhlig, F., Xu, A.B. Iterative optimal solutions of linear matrix equations for hyperspectral and multispectral image fusing. Calcolo 60, 26 (2023).      [https://doi.org/10.1007/s10092-023-00514-8](https://doi.org/10.1007/s10092-023-00514-8)
