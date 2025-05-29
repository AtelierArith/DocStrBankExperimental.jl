```
lyapcs!(A, E, C; adj = false)
```

Solve the generalized continuous Lyapunov matrix equation

```
            op(A)Xop(E)' + op(E)Xop(A)' + C = 0,
```

where `op(A) = A` and `op(E) = E` if `adj = false` and `op(A) = A'` and `op(E) = E'` if `adj = true`. The pair `(A,E)` is in a generalized real or complex Schur form and `C` is a symmetric or hermitian matrix. The pencil `A-λE` must not have two eigenvalues `α` and `β` such that `α+β = 0`. The computed symmetric or hermitian solution `X` is contained in `C`.
