```
nls = LLSModel(A, b; lvar, uvar, C, lcon, ucon)
```

Creates a Linear Least Squares model $\tfrac{1}{2}\|Ax - b\|^2$ with optional bounds `lvar ≦ x ≦ uvar` and optional linear constraints `lcon ≦ Cx ≦ ucon`. This problem is a nonlinear least-squares problem with residual given by $F(x) = Ax - b$.
