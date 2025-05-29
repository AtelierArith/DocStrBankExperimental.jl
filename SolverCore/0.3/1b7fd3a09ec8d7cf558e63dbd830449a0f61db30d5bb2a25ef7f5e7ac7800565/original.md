```
set_residuals!(stats::GenericExecutionStats{T, S, V}, primal::T, dual::T)
```

Register `primal` and `dual` as optimal primal and dual feasibility residuals, respectively, in `stats` and mark them as reliable.
