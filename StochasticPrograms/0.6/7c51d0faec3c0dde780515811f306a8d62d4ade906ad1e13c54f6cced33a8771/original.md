```
outcome_model(stochasticprogram::StochasticProgram{N},
              decisions::NTuple{N-1,AbstractVector}
              scenario_path::NTuple{N-1,AbstractScenario},
              optimizer = nothing)
```

Return the resulting `N`:th stage model if `decisions` are the decisions taken in the previous stages and `scenario_path` are the realized scenarios up to stage `N` in `stochasticprogram`. Optionally, supply a capable `solver` to the outcome model.
