```
set_primal_residual!(stats::GenericExecutionStats{T, S, V}, primal::T)
```

Register `primal` as optimal primal residuals in `stats` and mark it as reliable.
