```
prcplyap(A, C; K = 10, solver, reltol, abstol) -> U
```

Compute the upper triangular periodic factor `U(t)` of the solution `X(t) = U(t)'U(t)`

```
 .
-X(t) = A(t)'X(t) + X(t)A(t) + C(t)'C(t).
```

The periodic matrices `A` and `C` must have the same type, the same column dimensions and commensurate periods.  The resulting periodic factor `U` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

This function is merely an interface to [`pcplyap`](@ref) (see this function for the description of keyword parameters). 
