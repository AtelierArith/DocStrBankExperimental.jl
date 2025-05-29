```
prdplyap(A, C) -> U
```

Compute the upper triangular factor `U` of the solution `X = U'*U` of the  reverse time periodic discrete-time Lyapunov matrix equation

```
A'σXA + C'C = X
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`.  The periodic matrix `A` must be stable, i.e., have all characteristic multipliers  with moduli less than one. 

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods.  The resulting upper triangular periodic matrix `U` has the period  set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly.  

Note: `X` is the *observability Gramian* of the periodic pair `(A,C)`.              
