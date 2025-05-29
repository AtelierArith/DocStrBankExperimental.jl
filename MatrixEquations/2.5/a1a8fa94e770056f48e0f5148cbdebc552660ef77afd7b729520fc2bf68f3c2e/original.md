```
X = gsylvkr(A,B,C,D,E)
```

Solve the generalized Sylvester matrix equation

```
            AXB + CXD = E
```

using the Kronecker product expansion of equations. `A`, `B`, `C` and `D` are square matrices. The pencils `A-λC` and `D+λB` must be regular and must not have common eigenvalues. This function is not recommended for large order matrices.
