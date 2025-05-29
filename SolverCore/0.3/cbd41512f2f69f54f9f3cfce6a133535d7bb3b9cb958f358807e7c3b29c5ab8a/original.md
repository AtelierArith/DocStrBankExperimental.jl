```
set_dual_residual!(stats::GenericExecutionStats{T, S, V}, dual::T)
```

Register `dual` as optimal dual feasibility residuals in `stats` and mark it as reliable.
