```
X = sylvckr(A,B,C)
```

Solve the continuous Sylvester matrix equation

```
            AX + XB = C
```

using the Kronecker product expansion of equations. `A` and `B` are square matrices, and `A` and `-B` must not have common eigenvalues. This function is not recommended for large order matrices.
