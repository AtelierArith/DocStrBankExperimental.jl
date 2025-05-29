```
pfcplyap(A, B; K = 10, solver, reltol, abstol) -> U
```

Compute the upper triangular periodic factor `U(t)` of the solution `X(t) = U(t)U(t)'`

```
.
X(t) = A(t)X(t) + X(t)A(t)' + B(t)B(t)' .
```

The periodic matrices `A` and `B` must have the same type, the same row dimensions and commensurate periods.  The resulting periodic factor `U` has the period  set to the least common commensurate period of `A` and `B` and the number of subperiods is adjusted accordingly. 

This function is merely an interface to [`pcplyap`](@ref) (see this function for the description of keyword parameters). 
