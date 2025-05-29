```
all_decision_variables(stochasticprogram::StochasticProgram{N}, stage::Integer = 1) where N
```

Returns a list of all decisions currently in the `stochasticprogram` at `stage`. The decisions are ordered by creation time.
