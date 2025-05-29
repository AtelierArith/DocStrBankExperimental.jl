```
all_decision_variables(stochasticprogram::StochasticProgram{N}) where N
```

Returns a stage-wise list of all decisions currently in the `stochasticprogram`. The decisions are ordered by creation time. Defaults to the first stage.
