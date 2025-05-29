```
solve_time(model::Model)
```

利用可能な場合、ソルバーによって報告された解決時間を返します。属性が実装されていない場合は、「ArgumentError: ModelLike of type `Solver.Optimizer` does not support accessing the attribute MathOptInterface.SolveTimeSec()」を返します。
