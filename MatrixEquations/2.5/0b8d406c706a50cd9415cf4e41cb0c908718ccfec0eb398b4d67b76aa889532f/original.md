```
 cgls(A, b; shift, abstol, reltol, maxiter, x0) -> (x, info)
```

Solve `Ax = b` or minimize `norm(Ax-b)` using `CGLS`, the conjugate gradient method for unsymmetric linear equations and least squares problems.  `A` can be specified either as a rectangular matrix or as a linear operator, as defined in the `LinearMaps` package.   It is desirable that `eltype(A) == eltype(b)`, otherwise errors may result or additional allocations may occur in operator-vector products. 

The keyword argument `shift` specifies a regularization parameter as `shift = s`. If `s = 0` (default), then `CGLS` is Hestenes and Stiefel's specialized form of the conjugate-gradient method for least-squares problems. If `s ≠ 0`, the system `(A'*A + s*I)*b = A'*b` is solved. 

An absolute tolerance `abstol` and a relative tolerance `reltol` can be specified for stopping the iterative process (default: `abstol = 0`, `reltol = 1.e-6`).

The maximum number of iterations can be specified using `maxiter` (default: `maxiter = max(size(A),20)`).

An initial guess for the solution can be specified using the keyword argument vector `x0` (default: `x0 = missing`). 

The resulting named tuple `info` contains `(flag, resNE, iter)`, with convergence related information, as follows: 

```
 `info.flag`  - convergence flag with values:  
                1, if convergence occured; 
                2, if the maximum number of iterations has been reached without convergence;
                3, if the matrix `A'*A + s*I` seems to be singular or indefinite;
                4, if instability seems likely meaning `(A'*A + s*I)` indefinite and `norm(x)` decreased;  

 `info.resNE` - the relative residual for the normal equations `norm(A'*b - (A'*A + s*I)*x)/norm(A'*b)`;  

 `info.iter`  - the iteration number at which `x` was computed.
```

This function is a translation of the MATLAB implementation of `CGLS`, the conjugate gradient method for nonsymmetric linear equations and least squares problems [`https://web.stanford.edu/group/SOL/software/cgls/`](https://web.stanford.edu/group/SOL/software/cgls/).  The author of the code is Michael Saunders, with contributions from Per Christian Hansen, Folkert Bleichrodt and Christopher Fougner.    

*Note:*  Two alternative solvers `lsqr` and `lsmr`, available in the [`IterativeSolvers`](https://github.com/JuliaLinearAlgebra/IterativeSolvers.jl) package, can also be employed.  For example, the following call to `lsqr` can be alternatively used:

```
  using IterativeSolvers
  lsqr(A, b; kwargs...) -> x[, history]
```

where `kwargs` contains solver-specific keyword arguments. A similar call to  `lsmr` can be used.    
