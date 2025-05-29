```
X = sylvdkr(A,B,C)
```

Solve the discrete Sylvester matrix equation

```
            AXB + X = C
```

using the Kronecker product expansion of equations. `A` and `B` are square matrices, and `A` and `-B` must not have common reciprocal eigenvalues. This function is not recommended for large order matrices.
