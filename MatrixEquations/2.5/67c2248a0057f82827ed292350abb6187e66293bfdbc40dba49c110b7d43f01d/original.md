```
X = csylvckr(A,B,C)
```

Solve the continuous C-Sylvester matrix equation

```
            A*X + conj(X)*B = C
```

using the Kronecker product expansion of equations. `A`, `B` and `C` are `m×m`, `n×n` and `m×n` matrices, respectively, and `X` is an `m×n` matrix. This function is not recommended for large order matrices.
