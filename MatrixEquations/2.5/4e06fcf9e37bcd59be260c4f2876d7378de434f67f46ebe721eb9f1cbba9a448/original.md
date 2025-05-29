```
lyapcs!(A,C;adj = false)
```

Solve the continuous Lyapunov matrix equation

```
            op(A)X + Xop(A)' + C = 0,
```

where `op(A) = A` if `adj = false` and `op(A) = A'` if `adj = true`. `A` is a square real matrix in a real Schur form, or a square complex matrix in a complex Schur form and `C` is a symmetric or hermitian matrix. `A` must not have two eigenvalues `α` and `β` such that `α+β = 0`. `C` contains on output the solution `X`.
