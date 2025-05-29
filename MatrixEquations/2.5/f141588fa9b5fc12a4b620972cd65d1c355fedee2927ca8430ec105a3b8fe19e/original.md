```
plyapds!(A,E,R;adj = false)
```

Solve the generalized positive discrete Lyapunov matrix equation

```
            op(A)Xop(A)' - op(E)Xop(E)' + op(R)*op(R)' = 0
```

for `X = op(U)*op(U)'`, where `op(K) = K` if `adj = false` and `op(K) = K'` if `adj = true`. The pair `(A,E)` of square real or complex matrices is in a generalized Schur form and `R` is an upper triangular matrix. `A-λE` must have only eigenvalues with moduli less than one. `R` contains on output the upper triangular solution `U`.
