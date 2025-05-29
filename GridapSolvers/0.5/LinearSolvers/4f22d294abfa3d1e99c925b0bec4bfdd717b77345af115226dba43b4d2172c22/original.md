```
struct JacobiLinearSolver <: LinearSolver end
```

Given a matrix `A`, the Jacobi or Diagonal preconditioner is defined as `P = diag(A)`.
