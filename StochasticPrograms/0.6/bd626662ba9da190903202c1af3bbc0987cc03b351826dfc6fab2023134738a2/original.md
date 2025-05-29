```
objective_value(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

Return the objective value of the node at stage `stage` and scenario `scenario_index` associated with result index `result` of the most-recent solution after a call to `optimize!(stochasticprogram)`.
