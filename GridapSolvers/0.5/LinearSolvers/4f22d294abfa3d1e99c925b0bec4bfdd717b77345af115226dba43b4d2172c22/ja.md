```
struct JacobiLinearSolver <: LinearSolver end
```

行列 `A` に対して、ヤコビまたは対角前処理子は `P = diag(A)` と定義されます。
