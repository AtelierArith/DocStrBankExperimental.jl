```
solve(
    problem::GeneralBTPDE,
    gradient,
    odesolver = QNDF();
    abstol = 1e-6,
    reltol = 1e-4,
    callbacks = [].
)
```

Solve the Bloch-Torrey partial differential equation using P1 finite elements in space and `odesolver` in time.
