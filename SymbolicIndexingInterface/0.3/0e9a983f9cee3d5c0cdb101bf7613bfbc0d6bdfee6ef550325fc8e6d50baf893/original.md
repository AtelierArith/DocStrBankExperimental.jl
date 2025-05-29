```
finalize_parameters_hook!(valp, sym)
```

This is a callback run one for each call to the function returned by [`setp`](@ref) which can be used to update internal data structures when parameters are modified. This is in contrast to [`set_parameter!`](@ref) which is run once for each parameter that is updated.
