```
tsirelson_bound(FC::Array, level; verbose::Bool = false, dualize::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

Upper bounds the Tsirelson bound of a multipartite Bell funcional `FC`, written in correlation notation. `level` is an integer or a string like "1 + A B" determining the level of the NPA hierarchy. `verbose` determines whether solver output is printed. `dualize` determines whether the dual problem is solved instead. WARNING: This is critical for performance, and the correct choice depends on the solver.
