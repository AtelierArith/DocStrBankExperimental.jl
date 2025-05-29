```
(X,Y) = sylvsyss!(A,B,C,D,E,F)
```

Solve the Sylvester system of matrix equations

```
            AX + YB = C
            DX + YE = F,
```

where `(A,D)`, `(B,E)` are pairs of square matrices of the same size in generalized Schur forms. The pencils `A-λD` and `-B+λE` must be regular and must not have common eigenvalues. The computed solution `(X,Y)` is contained in `(C,F)`.

*Note:* This is an enhanced interface to the `LAPACK.tgsyl!` function to also cover the case when `A`, `B`, `D` and `E` are real matrices and `C` and `F` are complex matrices.
