```
pfclyap(A, C; K = 10, N = 1, solver, reltol, abstol, intpol) -> X
```

Solve the periodic forward-time Lyapunov differential equation

```
.
X(t) = A(t)X(t) + X(t)A(t)' + C(t) .
```

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods,  and additionally `C` must be symmetric. The resulting symmetric periodic solution `X` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

This function is merely an interface to [`pclyap`](@ref) (see this function for the description of keyword parameters). 
