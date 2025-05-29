```
set_constraint_multipliers!(stats::GenericExecutionStats{T, S, V}, y::S, zL::V, zU::V)
```

Register `y` as optimal multipliers associated to general constraints in `stats` and mark them as reliable.
