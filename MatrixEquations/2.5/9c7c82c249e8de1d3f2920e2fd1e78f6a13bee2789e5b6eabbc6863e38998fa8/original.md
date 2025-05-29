```
tulyapci(U, Q; adj = false, abstol, reltol, maxiter) -> (X,info)
```

Compute for an upper triangular `U` and a symmetric `Q` an upper triangular solution `X` of the continuous T-Lyapunov matrix equation

```
  transpose(U)*X + transpose(X)*U = Q   if adj = false,
```

or 

```
  U*transpose(X) + X*transpose(U) = Q   if adj = true.
```

For a `n×n` upper triangular matrix `U`, a least-squares upper-triangular solution `X` is determined using a conjugate-gradient based iterative method applied  to a suitably defined T-Lyapunov linear operator `L:X -> Y`, which maps upper triangular matrices `X` into upper triangular matrices `Y`, and the associated matrix `M = Matrix(L)` is $n(n+1)/2 \times n(n+1)/2$.  The keyword arguments `abstol` (default: `abstol = 0`) and `reltol` (default: `reltol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution.  The keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 1000`). 
