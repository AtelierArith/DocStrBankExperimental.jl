```
sylvsyskr(A,B,C,D,E,F) -> (X,Y)
```

Solve the Sylvester system of matrix equations

```
            AX + YB = C
            DX + YE = F
```

using the Kronecker product expansion of equations. `(A,D)`, `(B,E)` are pairs of square matrices of the same size. The pencils `A-λD` and `-B+λE` must be regular and must not have common eigenvalues. This function is not recommended for large order matrices.
