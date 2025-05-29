```
stage_probability(stochasticprogram::StochasticProgram, stage::Integer = 2)
```

Return the probability of any scenario in the `stochasticprogram` at `stage` occuring. A well defined model should return 1. Defaults to the second stage.
