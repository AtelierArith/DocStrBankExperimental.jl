```
X = gsylvs!(A,B,C,D,E; adjAC=false, adjBD=false, CASchur = false, DBSchur = false)
```

Solve the generalized Sylvester matrix equation

```
            op1(A)Xop2(B) + op1(C)Xop2(D) = E,
```

where `A`, `B`, `C` and `D` are square matrices, and

`op1(A) = A` and `op1(C) = C` if `adjAC = false`;

`op1(A) = A'` and `op1(C) = C'` if `adjAC = true`;

`op2(B) = B` and `op2(D) = D` if `adjBD = false`;

`op2(B) = B'` and `op2(D) = D'` if `adjBD = true`.

The matrix pair `(A,C)` is in a generalized real or complex Schur form. The matrix pair `(B,D)` is in a generalized real or complex Schur form if `DBSchur = false` or the matrix pair `(D,B)` is in a generalized real or complex Schur form if `DBSchur = true`. The pencils `A-λC` and `D+λB` must be regular and must not have common eigenvalues.
