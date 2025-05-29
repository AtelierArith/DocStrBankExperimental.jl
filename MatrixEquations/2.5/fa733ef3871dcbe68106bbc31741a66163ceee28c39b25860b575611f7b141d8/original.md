```
X = hsylvdkr(A,B,C)
```

Solve the discrete H-Sylvester matrix equation

```
            A*adjoint(X)*B + X = C
```

using the Kronecker product expansion of equations. `A`, `B` and `C` are `m×n` matrices and `X` is an `m×n` matrix. This function is not recommended for large order matrices.
