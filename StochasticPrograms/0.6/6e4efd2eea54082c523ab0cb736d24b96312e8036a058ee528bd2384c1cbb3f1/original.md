```
relative_gap(model::StochasticProgram, stage::Integer, scenario_index::Integer)
```

Return the final relative optimality gap in the node at stage `stage` and scenario `scenario_index` after a call to `optimize!(stochasticprogram)`.
