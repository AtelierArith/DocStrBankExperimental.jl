```
add_scenario!(scenariogenerator::Function, stochasticprogram::StochasticProgram)
```

Store the scenario returned by `scenariogenerator` in the two-stage `stochasticprogram`. If the `stochasticprogram` is distributed, the scenario will be defined on the node that currently has the fewest scenarios.
