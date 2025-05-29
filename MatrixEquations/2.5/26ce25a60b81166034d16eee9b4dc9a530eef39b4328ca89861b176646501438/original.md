```
(X,Y) = dsylvsyss!(A,B,C,D,E,F)
```

Solve the dual Sylvester system of matrix equations

```
A'X + D'Y = C
XB' + YE' = F,
```

where `(A,D)`, `(B,E)` are pairs of square matrices of the same size in generalized Schur forms. The pencils `A-λD` and `-B+λE` must be regular and must not have common eigenvalues. The computed solution `(X,Y)` is contained in `(C,F)`.
