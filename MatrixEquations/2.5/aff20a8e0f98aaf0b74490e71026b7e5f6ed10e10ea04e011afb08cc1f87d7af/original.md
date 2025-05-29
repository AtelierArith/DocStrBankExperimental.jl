```
X = csylvdkr(A,B,C)
```

Solve the discrete C-Sylvester matrix equation

```
            A*conj(X)*B + X = C
```

using the Kronecker product expansion of equations. `A`, `B` and `C` are `m×m`, `n×n` and `m×n` matrices, respectively, and `X` is an `m×n` matrix. This function is not recommended for large order matrices.
