```
solver_name(model::Model)
```

利用可能な場合、基盤となる最適化ツールの `SolverName` プロパティを返します。

最適化ツールが接続されていない場合、`AUTOMATIC` または `MANUAL` モードでは `"No optimizer attached"` を返します。

属性が実装されていない場合は、`"SolverName() attribute not implemented by the optimizer."` を返します。
