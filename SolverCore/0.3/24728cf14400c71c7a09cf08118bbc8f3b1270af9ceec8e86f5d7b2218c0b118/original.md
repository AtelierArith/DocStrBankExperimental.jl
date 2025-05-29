```
set_multipliers!(stats::GenericExecutionStats{T, S, V}, y::S, zL::V, zU::V)
```

Register `y`, `zL` and `zU` as optimal multipliers associated to general constraints, lower-bounded and upper-bounded constraints, respectively, in `stats` and mark them as reliable.
