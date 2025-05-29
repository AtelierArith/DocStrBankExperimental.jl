```
get_variable_description(label::Symbol, database::TelemetryDatabase) -> TelemetryVariableDescription
```

Get the description of a variable with `label` in `database`. Notice that `label` can also be the variable alias. If the variable is not found, the function returns `nothing`.
