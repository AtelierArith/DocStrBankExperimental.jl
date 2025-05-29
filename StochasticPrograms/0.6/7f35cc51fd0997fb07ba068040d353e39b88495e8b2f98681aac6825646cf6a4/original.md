```
add_scenarios!(scenariogenerator::Function, stochasticprogram::StochasticProgram, stage::Integer, n::Integer)
```

Generate `n` scenarios using `scenariogenerator` and store in the `stochasticprogram` at `stage`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
