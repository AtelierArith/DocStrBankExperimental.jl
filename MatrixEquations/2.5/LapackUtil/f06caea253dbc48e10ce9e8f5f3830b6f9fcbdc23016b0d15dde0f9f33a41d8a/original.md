```
tgsyl!(A, B, C, D, E, F) -> (C, F, scale)
```

Solve the Sylvester system of matrix equations

```
  AX - YB = scale*C
  DX - YE = scale*F ,
```

where `X` and `Y` are unknown matrices, the pairs `(A, D)`, `(B, E)` and  `(C, F)` have the same sizes, and the pairs `(A, D)` and `(B, E)` are in generalized (real) Schur canonical form, i.e. `A`, `B` are upper quasi triangular and `D`, `E` are upper triangular. Returns `X` (overwriting `C`), `Y` (overwriting `F`) and `scale`.

```
tgsyl!(trans, A, B, C, D, E, F) -> (C, F, scale)
```

Solve for `trans = 'T'` and real matrices or for `trans = 'C'` and complex matrices,  the (adjoint) Sylvester system of matrix equations

```
  A'X + D'Y = scale*C
  XB' + YE' = scale*(-F) .
```

`tgsyl!('N', A, B, C, D, E, F)` corresponds to the call `tgsyl!(A, B, C, D, E, F)`.

Interface to the LAPACK subroutines DTGSYL/STGSYL/ZTGSYL/CTGSYL.
