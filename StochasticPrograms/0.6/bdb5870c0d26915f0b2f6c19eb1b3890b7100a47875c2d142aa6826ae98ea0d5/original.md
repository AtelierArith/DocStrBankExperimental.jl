```
objective_value(stochasticprogram::TwoStageStochasticProgram, scenario_index::Integer; result::Int = 1)
```

Return the objective value of scenario `scenario_index` associated with result index `result` of the most-recent solution after a call to `optimize!(stochasticprogram)`.
