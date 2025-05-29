```
solve_time(model::Model)
```

If available, returns the solve time reported by the solver. Returns "ArgumentError: ModelLike of type `Solver.Optimizer` does not support accessing the attribute MathOptInterface.SolveTimeSec()" if the attribute is not implemented.
