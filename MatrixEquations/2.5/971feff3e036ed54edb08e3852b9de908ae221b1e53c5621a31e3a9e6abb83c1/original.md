```
plyapcs!(A,R;adj = false)
```

Solve the positive continuous Lyapunov matrix equation

```
            op(A)X + Xop(A)' + op(R)*op(R)' = 0
```

for `X = op(U)*op(U)'`, where `op(K) = K` if `adj = false` and `op(K) = K'` if `adj = true`. `A` is a square real matrix in a real Schur form  or a square complex matrix in a complex Schur form and `R` is an upper triangular matrix. `A` must have only eigenvalues with negative real parts. `R` contains on output the solution `U`.
