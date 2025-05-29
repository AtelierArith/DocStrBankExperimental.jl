```
add_scenario!(stochasticprogram::StochasticProgram, stage::Integer, scenario::AbstractScenario)
```

Store the second stage `scenario` in the `stochasticprogram` at `stage`.

If the `stochasticprogram` is distributed, the scenario will be defined on the node that currently has the fewest scenarios.
