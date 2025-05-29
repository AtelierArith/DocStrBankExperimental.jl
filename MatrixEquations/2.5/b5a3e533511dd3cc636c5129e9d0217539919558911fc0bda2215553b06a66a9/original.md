```
tlyapci(A, C, isig = +1; adj = false, abstol, reltol, maxiter) -> (X,info)
```

Compute a solution `X` of the continuous T-Lyapunov matrix equation

```
            A*X +isig*transpose(X)*transpose(A) = C   if adj = false,
```

or

```
            A*transpose(X) + isig*X*transpose(A) = C   if adj = true,
```

where for `isig = 1`, `C` is a symmetric matrix and for `isig = -1`, `C` is a skew-symmetric matrix.                     

For a matrix `A`, a least-squares solution `X` is determined using a conjugate gradient based iterative method applied  to a suitably defined T-Lyapunov linear operator `L:X -> Y` such that `L(X) = C` or `norm(L(X) - C)` is minimized.  The keyword arguments `abstol` (default: `abstol = 0`) and `reltol` (default: `reltol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution and  the keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 1000`). 
