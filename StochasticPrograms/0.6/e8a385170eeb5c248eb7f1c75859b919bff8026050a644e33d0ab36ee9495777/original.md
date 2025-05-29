```
outcome_model(stochasticprogram::TwoStageStochasticProgram,
              decision::AbstractVector,
              scenario::AbstractScenario;
              optimizer = nothing)
```

Return the resulting second stage model if `decision` is the first-stage decision in the provided `scenario`, in `stochasticprogram`. The supplied `decision` must match the defined decision variables in `stochasticprogram`. Optionally, supply a capable `optimizer` to the outcome model.
