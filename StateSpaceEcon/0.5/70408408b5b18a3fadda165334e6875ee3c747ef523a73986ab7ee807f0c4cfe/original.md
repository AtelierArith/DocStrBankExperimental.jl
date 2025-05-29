```
solve!(m::Model; [solver::Symbol])
```

Solve the given model and update its `m.solverdata` according to the specified solver.  The solver is specified as a `Symbol`.  The default is `solve=:stackedtime`.
