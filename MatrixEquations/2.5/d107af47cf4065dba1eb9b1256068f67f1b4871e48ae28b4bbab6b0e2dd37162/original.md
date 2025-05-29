```
lyapdi(A, E, C; abstol, reltol, maxiter) -> (X,info)
```

Compute `X`, the solution of the generalized discrete Lyapunov equation

```
AXA' - EXE' + C = 0,
```

where `A` and `E` are square real or complex matrices and `C` is a square matrix. A least-squares solution `X` is determined using a conjugate gradient based iterative method applied  to a suitably defined Lyapunov linear operator `L:X -> Y` such that `L(X) = C` or `norm(L(X) - C)` is minimized.  The keyword arguments `abstol` (default: `abstol = 0`) and `reltol` (default: `reltol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution and  the keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 1000`). 
