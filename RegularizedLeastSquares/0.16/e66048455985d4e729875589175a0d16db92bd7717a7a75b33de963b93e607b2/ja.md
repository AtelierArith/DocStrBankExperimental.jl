```
createLinearSolver(solver::AbstractLinearSolver, A; kargs...)
```

このメソッドはソルバーを作成します。サポートされているソルバーは、通常、正則化された線形システムを解くために使用されるメソッドです。すべてのソルバーは、Ax = bの近似解を返します。

TODO: 利用可能なソルバーについてのヒントを提供する
