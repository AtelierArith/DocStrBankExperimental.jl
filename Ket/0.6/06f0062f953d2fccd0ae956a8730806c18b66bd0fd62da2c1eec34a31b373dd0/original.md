```
tsirelson_bound(CG::Array, scenario::Tuple, level; verbose::Bool = false, dualize::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

Upper bounds the Tsirelson bound of a multipartite Bell funcional `CG`, written in Collins-Gisin notation. `scenario` is a tuple detailing the number of inputs and outputs, in the order (oa, ob, ..., ia, ib, ...). `level` is an integer or a string like "1 + A B" determining the level of the NPA hierarchy. `verbose` determines whether solver output is printed. `dualize` determines whether the dual problem is solved instead. WARNING: This is critical for performance, and the correct choice depends on the solver.
