```
set_bounds_multipliers!(stats::GenericExecutionStats{T, S, V}, zL::V, zU::V)
```

Register `zL` and `zU` as optimal multipliers associated to lower-bounded and upper-bounded constraints, respectively, in `stats` and mark them as reliable.
