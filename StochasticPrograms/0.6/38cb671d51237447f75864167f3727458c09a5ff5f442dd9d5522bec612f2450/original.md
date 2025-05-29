```
objective_bound(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer)
```

Return the best known bound on the optimal objective value in the node at stage `stage` and scenario `scenario_index` after a call to `optimize!(stochasticprogram)`.
