```
set_solver_specific!(stats::GenericExecutionStats, field::Symbol, value)
```

Register `value` as a solver-specific value identified by `field` in `stats` and mark it as reliable.
