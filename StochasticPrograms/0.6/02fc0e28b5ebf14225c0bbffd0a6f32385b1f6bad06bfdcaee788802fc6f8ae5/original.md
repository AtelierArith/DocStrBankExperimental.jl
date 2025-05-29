```
add_scenarios!(stochasticprogram::StochasticProgram, stage::Integer, scenarios::Vector{<:AbstractScenario})
```

Store the collection of `scenarios` in the `stochasticprogram` at `stage`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
