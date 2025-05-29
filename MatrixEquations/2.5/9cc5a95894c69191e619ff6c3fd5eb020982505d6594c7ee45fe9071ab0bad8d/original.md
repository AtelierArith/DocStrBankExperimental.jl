```
sylvds!(A,B,C; adjA = false, adjB = false)
```

Solve the discrete Sylvester matrix equation

```
            op(A)Xop(B) + X =  C,
```

where `op(A) = A` or `op(A) = A'` if `adjA = false` or `adjA = true`, respectively, and `op(B) = B` or `op(B) = B'` if `adjB = false` or `adjB = true`, respectively. `A` and `B` are square matrices in Schur forms, and `A` and `-B` must not have common reciprocal eigenvalues. `C` contains on output the solution `X`.
