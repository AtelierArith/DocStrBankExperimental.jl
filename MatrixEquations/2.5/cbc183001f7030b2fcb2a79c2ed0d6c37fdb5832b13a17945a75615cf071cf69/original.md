```
lyapds!(A, C; adj = false)
```

Solve the discrete Lyapunov matrix equation

```
            op(A)Xop(A)' - X + C = 0,
```

where `op(A) = A` if `adj = false` and `op(A) = A'` if `adj = true`. `A` is in a real or complex Schur form and `C` is a symmetric or hermitian matrix. `A` must not have two eigenvalues `α` and `β` such that `αβ = 1`. The computed symmetric or hermitian solution `X` is contained in `C`.
