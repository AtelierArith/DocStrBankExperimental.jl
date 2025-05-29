```
plyapcs!(A,E,R;adj = false)
```

Solve the generalized positive continuous Lyapunov matrix equation

```
            op(A)Xop(E)' + op(E)*Xop(A)' + op(R)*op(R)' = 0
```

for `X = op(U)*op(U)'`, where `op(K) = K` if `adj = false` and `op(K) = K'` if `adj = true`. The pair `(A,E)` is in a generalized real/complex Schur form and `R` is an upper triangular matrix. The pencil `A-λE` must have only eigenvalues with negative real parts. `R` contains on output the solution `U`.
