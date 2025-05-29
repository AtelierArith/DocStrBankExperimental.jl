```
default_logger()
```

Return the current value of the default logger for use with supported machine learning tracking platforms, such as [MLflow](https://mlflow.org/docs/latest/index.html).

The default logger is used in calls to [`evaluate!`](@ref) and [`evaluate`](@ref), and in the constructors `TunedModel` and `IteratedModel`, unless the `logger` keyword is explicitly specified.

!!! note
    Prior to MLJ v0.20.7 (and MLJBase 1.5) the default logger was always `nothing`.


When MLJBase is first loaded, the default logger is `nothing`.
