```
kron_axpy!(A, X, Y)
```

Overwrite `Y` with `A ⊗ X + Y`. Same as `Y += kron(A, X)` but more memory efficient.
