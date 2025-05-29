```
add_scenarios!(scenariogenerator::Function, stochasticprogram::TwoStageStochasticProgram, n::Integer)
```

Generate `n` scenarios using `scenariogenerator` and store in the two-stage `stochasticprogram`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
