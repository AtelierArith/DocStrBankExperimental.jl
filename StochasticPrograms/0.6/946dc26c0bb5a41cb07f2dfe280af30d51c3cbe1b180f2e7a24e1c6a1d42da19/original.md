```
has_duals(stochasticprogram::TwoStageStochasticProgram, scenario_index::Integer; result::Int = 1)
```

Return `true` if the solver has a dual solution in scenario `scenario_index` in result index `result` available to query, otherwise return `false`.
