```
enable_inline_stability_checks(::Bool)
```

Sets whether to run inline stability checks from [`@stable_function`](@ref).

If it is set to `false` (the default value), @stable_function does not perform any type stability checks.

The value is checked when @stable_function is evaluated, so this should useually be set at the begining of a package definition.

See [`inline_stability_checks_enabled`](@ref).
