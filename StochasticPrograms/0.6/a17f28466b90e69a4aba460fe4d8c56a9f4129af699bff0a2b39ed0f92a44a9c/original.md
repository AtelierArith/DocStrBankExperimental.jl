```
add_scenario!(scenariogenerator::Function, stochasticprogram::StochasticProgram, stage::Integer)
```

Store the scenario returned by `scenariogenerator` in the `stage` of the `stochasticprogram`. If the `stochasticprogram` is distributed, the scenario will be defined on the node that currently has the fewest scenarios.
