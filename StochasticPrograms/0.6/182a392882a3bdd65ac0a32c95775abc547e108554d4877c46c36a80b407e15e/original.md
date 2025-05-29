```
has_duals(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

Return `true` if the solver has a dual solution in the node at stage `stage` and scenario `scenario_index` in result index `result` available to query, otherwise return `false`.
