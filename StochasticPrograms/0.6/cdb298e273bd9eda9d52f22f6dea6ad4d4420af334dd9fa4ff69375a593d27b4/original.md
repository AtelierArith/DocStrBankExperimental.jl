```
add_scenarios!(stochasticprogram::TwoStageStochasticProgram, scenarios::Vector{<:AbstractScenario})
```

Store the collection of `scenarios` in the two-stage `stochasticprogram`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
