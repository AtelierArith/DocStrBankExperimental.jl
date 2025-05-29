```
pfdplyap(A, B) -> U
```

Compute the upper triangular factor `U` of the solution `X = U*U'` of the  forward-time periodic discrete-time Lyapunov equation

```
AXA' + BB' = σX
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`.   The periodic matrix `A` must be stable, i.e., have all characteristic multipliers  with moduli less than one. 

The periodic matrices `A` and `B` must have the same type, the same dimensions and commensurate periods.  The resulting upper triangular periodic matrix `U` has the period  set to the least common commensurate period of `A` and `B` and the number of subperiods is adjusted accordingly.  

Note: `X` is the *reachability Gramian* of the periodic pair `(A,B)`.              
