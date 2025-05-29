```
variableimportance(model, folds, variable; reps=10, optimality=mcc, kwargs...)
```

Returns the importance of one variable in the model. The `samples` keyword fixes the number of bootstraps to run (defaults to `10`, which is not enough!).

The keywords are passed to `ConfusionMatrix`.
