```
create_linsolver(creator::LinSovlerCreator,nep,λ)
```

`λ`で評価される`nep`に対応する`LinSolver`インスタンスを作成します。出力の型はディスパッチと`LinSolverCreator`の型によって決まります。

関連情報: `LinSolver`, `FactorizeLinSolverCreator`, `BackslashLinSolverCreator`, `DefaultLinSolverCreator`, `GMRESLinSolverCreator`.
