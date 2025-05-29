```
log_parameter_information(
    pd::AbstractTOMLDict,
    filepath;
    strict::Bool = false
)
```

Writes the parameter log file at `filepath`; checks that override parameters are all used.

If `strict = true`, errors if override parameters are unused.
