```
X = sylvci(A,B,C)
```

Solve the continuous Sylvester matrix equation

```
            AX + XB = C ,
```

where `A` and `B` are square matrices. 

A least-squares solution `X` is determined using a conjugate gradient based iterative method applied  to a suitably defined Lyapunov linear operator `L:X -> Y` such that `L(X) = C` or `norm(L(X) - C)` is minimized.  The keyword arguments `abstol` (default: `abstol = 0`) and `reltol` (default: `reltol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution and  the keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 1000`). 
